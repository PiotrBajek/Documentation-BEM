# Documentation BEM

* Block
* Element `__`
* Modifier(s) `--``

```html
<header class="header">
  <nav class="headerNav">
    <ul class="headerNav">
      <li class="headerNav__item">
        <a href="/a-propos" class="headerNav__itemLink">
          A propos
        </a>
      </li>
      <li class="headerNav__item">
        <a href="/home" class="headerNav__itemLink headerNav__itemLink--isActive">
          Accueil
        </a>
      </li>
      <li class="headerNav__item">
        <a href="/account" class="headerNav__itemLink headerNav__itemLink--isDisabled">
          Mon compte
        </a>
      </li>
    </ul>
  </nav>
</header>
```

```css
$bptablet: 768px;
$bpdesktop: 1024px;

@mixin bp(val) {
  @media (min-width: #{val}) {
    @content;
  }
}
.headerNav {
  display: flex;
  justify-content: space-between;
  @include bp($bptablet) {
    flex-direction: column;
  }
  &--xmas {
    background: red;
  }
  &__item {
    list-style: none;
  }
  &__itemLink {
    color: #fff;
    text-decoration: none;
    &--isDisabled {
      color: grey;
    }
    &--isActive {
      color: green;
    }
  }
}
```

# Psuedo attribut ::after & ::before

Les pseudos attributs `before`et `after` sont essentiellment utilisés pour
ajouter des éléments à votre Dom pour décorer sans que cela ait un impact sur
le référencement ou votre HTML.

### **ATTENTION**

* Il est obligatoire d'avoir un `content: ''` afin que vos after / before s'affichent.
* Vous pouvez leur donnez une taille, une position (absolute par rapport à son parent)
* essentiellment utilisé pour de la décoration.  

```HTML
<section class="cover">
  <h2 class="cover__title">Présentation</h2>
</section>
```

```css
.cover {
  &__title {
    font-size: 24px;
    color: #bbb;
    text-align: center;
    position: relative;
    &::before,
    &::after {
      content: '';
      position: absolute;
      top: 0;
      display: block;
      width: 50px;
      height: 50px;
      background: green;
    }
    &::before {
      left: 0;
    }
    &::after {
      right: 0;
    }
  }
}
```

## Why SCSS is better than CSS with BEM

```CSS
.nav {

}
.nav__list {

}
.nav__list__item {

}
.nav__link {

}
.nav__link--active {

}
```

## Les unités

### REM

L'unité de mesure REM est basée sur la taille de l'élément racine du HTML.
Par défaut, la taille du `<html>` est sde 16px, ce qui veut dire que `1rem = 16px`.
Pour éviter de devoir faire des calculs afin de respecter les tailles relatives à votre
maquette, vous pouvez ré-écrire cette `font-size` afin que `1rem = 10px`

Les proportions et tailles vont se scaler en fonction du zoom de la page.

```css
  html {
    font-size: 62,5%;
  }

  .mainTitle {
    font-size: 2.4rem;
  }

  .cover {
    width: 32rem;
  }

```

### EM

Le `EM` à contrario du `REM` se base quant à lui sur la taille de son parent direct (pas son grand-parent).

```css
.cover {
  font-size: 16px
  &__title {

  }
}
```

## vm

## Les Grilles avec Flexboxgrid

# [Documentation](http;//flexboxgrid.com/)


### CssNext

#[Lien](https://github.com/MoOx/postcss-cssnext/)
