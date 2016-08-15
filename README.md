# Components-code-style-standard
Name properties/attributes, methods, events and behaviours as the comunity dose.
Applicable for any library/framework based on components.

## Why this
Everyone has their own way to code or name their functions/methods. That makes it difficult to follow/understand the internal code of a component if you and the creator follow different conventions to organise the code, name the methods, events... 

That can be even more confusing if you want to modify their component.

Let's end up with this problem with this standard.

## React specification

### Components

### Files

#### Structure

### Events

## Flux

## Ember specification

### Holy example

```javascript
/*
 - name the component with at least one dash
 - use subfolders to organise your components
 - use names that make sense
 */
//video-player/progress-bar/button-holder.js

/*import libraries at the very top*/
import Ember from 'ember';

/*you could declare other variables here depending on the scenario
...try to keep the code inside the component or declare it somewhere else*/

export default Ember.Component.extend({
  /* declare undefined variables at the very top */
  secondsDuration: undefined,
  /* declare undefined variables at the very top */
  widthProgressBar: 0,
  widthBar: 0,
  mouseMoveOffsetX: 0,
  userIsDragging: false,

  progressButtonStyle: Ember.computed('widthBar', 'mouseMoveOffsetX', function() {
    let style;
    if (this.get('userIsDragging')) {
      style = Ember.String.htmlSafe("left: " + this.get('mouseMoveOffsetX') + "px");
    } else {
      style = Ember.String.htmlSafe("left: " + this.get('widthBar') + "%");
    }

    return style;
  }),

  mouseMoveOffsetXObserver: Ember.observer('mouseMoveOffsetX', function () {
    this.get('onChangeMouseMoveOffsetX')();
  }),

  mouseDown () {
    this.followMousePosition();

    this.set('userIsDragging', true);
  },

  followMousePosition () {
    let $body = $('body');

    $body.on('mousemove', (e) => {
      this.set('mouseMoveOffsetX', e.pageX);
    }).on('mouseup', () => {
      this.set('userIsDragging', false);
      this.updateTimeByClickedPosition(this.get('mouseMoveOffsetX'));
      //this.get('onMouseDrop')(this.get('mouseMoveOffsetX'));
      $body.off('mousemove').off('mouseup');
    });
  },

  updateTimeByClickedPosition (position) {
    this.get('onChangeSecondsTime')(position);
  }
});

```

### Components

### Files

### Actions

## Angular 2


## Other standards or documents of interest
https://github.com/airbnb/javascript/tree/master/react

## TODO
- [x] Draft
- [ ] Logo
- [ ] Ember
- [ ] React
- [ ] Flux
- [ ] ESLint plugin?

## References
