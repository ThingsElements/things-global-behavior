# things-global-behavior

## This is a Behavior that makes Set/Get of global variables connectable through Elements.

In the samples below, we modified it in test-2, but it is also detected in test-1 thus printed on the console.

Example:
```html
<test-1></test-1>
<test-2></test-2>

<dom-module id="test-1">
  <template>
    <style>
      :host {
        display: block;
      }
    </style>

  </template>
  <script>
    Polymer({
      is: 'test-1',
      behavior:[
        Things.GlobalBehavior
      ],
      observers:[
        'onGlobalsChange(globals.*)'
      ],
      onGlobalsChange: function(a,b,c){
        console.log(a,b,c)
      }
    });
  </script>
</dom-module>

<dom-module id="test-2">
  <template>
    <style>
      :host {
        display: block;
      }
    </style>

  </template>
  <script>
    Polymer({
      is: 'test-2',
      behavior:[
        Things.GlobalBehavior
      ],
      observers:[
        'onGlobalsChange(globals.*)'
      ],
      onGlobalsChange: function(a,b,c){
        console.log(a,b,c)
      },
      attached: function(){
        this.set('globals.a','ABC')
      }
    });
  </script>
</dom-module>
```

## Dependencies

Element dependencies are managed via [Bower](http://bower.io/). You can install that via:

    npm install -g bower

Then, go ahead and download the element's dependencies:

    bower install


## Playing With Your Element

If you wish to work on your element in isolation, we recommend that you use
[Polyserve](https://github.com/PolymerLabs/polyserve) to keep your element's
bower dependencies in line. You can install it via:

    npm install -g polymer-cli

And you can run it via:

    polymer serve

Once running, you can preview your element at
`http://localhost:8080/components/things-global-behavior/`, where `things-global-behavior` is the name of the directory containing it.
