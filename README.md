## Setting up Custom Elements with Polymer

From project directory install Polymer library

````
bower install Polymer/polymer
````

Create your component and import polymer dependencies and shared or custom styles

````html
<link rel="import" href="/bower_components/polymer/polymer-element.html">
<link rel="import" href="shared-styles.html">
<link rel="import" href="custom-styles.html">

<!-- dom module -->
<dom-module id="custom-element">
    <template>
        <style include="shared-styles"></style>
        <div>Custom Element</div>
    </template>

    <script>
        /** @polymerElement */
        class CustomElement extends Polymer.Element {
            static get is() {
                return 'custom-element';
            }
            static get properties() {
                return {
                    prop1: {
                        type: String,
                        value: 'custom-element'
                    }
                };
            }
        }

        window.customElements.define(CustomElement.is, CustomElement);
    </script>

</dom-module>
````

Whenever you want to use your custom element include it in the page and then reference it using the element's tag

````html
<!DOCTYPE html>
<html>
    <head>
        <link rel="import" href="custom-element.html">
    </head>
<body>

<custom-element></custom-element>
````

When using custom CSS mixins like `@apply` you need to use the `custom-style` tag
