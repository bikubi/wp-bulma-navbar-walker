# WPBulmaNavbarWalker

A WordPress [Nav Walker](https://developer.wordpress.org/reference/classes/walker_nav_menu/) that outputs markup for the [Bulma Navbar Component](https://bulma.io/documentation/components/navbar/).  
Supports sub-menus/dropdowns.

## Usage

```php
<nav class="navbar">
  <div class="navbar-brand">
    ...
  </div>
  <div class="navbar-menu">
    <div class="navbar-end"><?php
      if (has_nav_menu('primary_navigation')) {
        wp_nav_menu(array(
          'theme_location' => 'foo',
          'menu_class'     => '',     // ignored
          'container'      => '',     // ignored
          'menu_class'     => '',     // ignored
          'items_wrap'     => '%3$s', // NOT ignored
          'walker'         => new \Bikubi\WPBulmaNavbarWalker\Walker_Nav_Menu
        ));
      }
    ?></div>
  </div>
</nav>
```

## Notes

- Inspired by [github.com/ridgey28/WP-Bulma-Navwalker](https://github.com/ridgey28/WP-Bulma-Navwalker). It almost worked for me but I ran into problems with functions that use the `walker_nav_menu_start_el` filter and depend on `$args` being a `stdClass` object. YMMV.
- I just found [saffa803/sage-bulma-navwalker/blob/master/bulma-navwalker.php](https://github.com/saffa803/sage-bulma-navwalker/blob/master/bulma-navwalker.php). Sigh. It uses `<li>`s which need some extra CSS to be presented in a row (that is, a `navbar`).
