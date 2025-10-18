# NAME

Mojolicious::Plugin::FontAwesomeHelpers - Mojolicious helpers for Font Awesome icons

# SYNOPSIS

    # template.html.ep
    %= icon 'fas fa-chevron' # => <i class="fas fa-chevron" aria-hidden="true"></i>
    %= icon 'fas fa-chevron', 'Back' # => <i class="fas fa-chevron" aria-hidden="true"></i> Back

    # ViewModel.pm
    package ViewModel {
      # ... other methods
      sub fa_class { 'fas fa-circle' }
    }

    # another_template.html.ep
    %= icon ViewModel->new # => <i class="fas fa-circle" aria-hidden="true"></i>
    %= icon ViewModel->new, 'A Circle' # => <i class="fas fa-circle" aria-hidden="true"></i> A Circle

# HELPERS

## icon

    %= icon 'fas fa-chevron' # => <i class="fas fa-chevron" aria-hidden="true"></i>
    %= icon 'fas fa-chevron', 'Back' # => <i class="fas fa-chevron" aria-hidden="true"></i> Back

    %= icon ViewModel->new # => <i class="fas fa-circle" aria-hidden="true"></i>
    %= icon ViewModel->new, 'A Circle' # => <i class="fas fa-circle" aria-hidden="true"></i> A Circle

    %= icon 'fas fa-chevron', (id => 'back', class => 'fa-solid'), 'Back'
      # => <i id="back", class="fas fa-chevron fa-solid" aria-hidden="true"></i> Back

    %= icon 'fas fa-chevron' => begin
     <b>Back</b>
    %= end
      # => <i class="fas fa-chevron aria-hidden="true"></i> <b>Back</b>

Renders a Font Awesome icon using an `i` tag. It will also handle accessibility
concerns.

It can be used with two string arguments specifying the icon style and name
respectively. A third argument can be given to specify text that should be rendered
adjacent to the icon.

If the first argument is an object that implements a `fa_class` method then the
return value of that method will be used to specify the icon and a second argument,
if provided, will be rendered as text adjacent to the icon.

All other arguments will be rendered as HTML attributes on the `i` tag.

## fa\_icon

    %= fa_icon 'fas fa-circle' # => "<i class="fas fa-circle" aria-hidden="true"></i>

An alias of ["icon"](#icon).

## fa->icon

    %= $c->fa->icon('fas fa-circle') # => "<i class="fas fa-circle" aria-hidden="true"></i>

An alias of ["icon"](#icon).

## stacked\_icon

    %= stacked_icon -size => '2x' => begin
      %= icon 'fa-solid fa-square', -stack => '2x'
      %= icon 'fab fa-twitter', -stack => '1x', :inverse
    %= end

## fa\_stack

An alias of ["stacked\_icon"](#stacked_icon)

## fa->stack

An alias of ["stacked\_icon"](#stacked_icon)

## fa->class

    %= $c->fa->class('fas fa-circle') # => "fas fa-circle"
    %= $c->fa->class('fas fa-circle', -size => 'sm') # => "fas fa-circle fa-sm"

    %= $c->fa->class(ViewModel->new) # => "fas fa-circle"
    %= $c->fa->class(ViewModel->new, -size => 'sm') # => "fas fa-circle fa-sm"

### Options

#### -size

#### -rotate

#### -flip

#### -stack

#### -inverse

#### -beat

#### -fade

#### -beat & -fade

#### -bounce

#### -shake

#### -spin

#### -pull

#### -width

#### -opacity
