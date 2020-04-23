# Selector
## Universal Selector
```css
/* DO NOT USE UNIVERSAL SELECTOR */
* {
    property: value;
}
```

## Element Selector
```css
element {
    property: value;
}
```

## Class Selector
```css
.class {
    property: value;
}
```

## ID Selector
```css
#identifier {
    property: value;
}
```

## Group Selector
```css
element, element {
    property: value;
}
```

## Child Selector
Child selector target the only directly child element in the parent element.
```css
parent > child {
    property: value;
}
```

## Descendant Selector
Descendant selector target all child element in the parent element.
```css
element1 element2 {
    property: value;
}
```