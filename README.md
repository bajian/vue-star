# vue-star

> A Vue2.0 project

## Build DEMO Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

```


Base on [VueStar](https://github.com/OYsun/VueStar) .
>感谢原作者！无意冒犯。因为我的改动太大，所以没有fork来pr，也没有发布到npm。就自用并分享出来。


#### How to install from code source 
``` js
import star from './components/vue-star'
...
components: {
    star
  },

<star :active="state" 
      @on-toggle="onToggle" 
      @on-animation-end="onAnimationEnd"  
      animate="animated rubberBand">
    <i slot="icon" class="fa fa-heart fa-2x"></i> 
</star>
```


## Api
### Properties
| Name                 | Type      | Default      | Description                                                        |
|----------------------|-----------|--------------|------------------------------------------------------------------|
| animate   | `String` | `''`       | the  animation class name, you can add animation CSS class from the CSS animation library, such as : https://github.com/daneden/animate.css |
| color   | `String` | `''`      | the color when the star is active state (hex or rgb color code) |
| active      | `Boolean` | `false`      | the state of the star . U can also change it to set the initial state 
| decorationClass      | `String` | `''`      | the exrate class of the decoration if needed
| ==================== | ========= | ============ | =================== |

### slot
| Name                 | Description                                                        |
|----------------------|-----------|--------------|------------------------------------------------------------------|
| icon   | the slot of the icon . it is suggetsed to use the font-awesome : https://github.com/FortAwesome/Font-Awesome |

| ==================== | ========= | ============ | =================== |

### Events
| Name                            | Parameters | Description                                                                                                                                                  |
|--------------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| on-toggle | `state`     | Fire after the toggle of the star state . `state` is Boolean                                |
| on-animation-end   | no     |   Fire after the  animation end                                                                   |

| ================== | ================ | ============================ |

### Methods
| Name                            | Parameters | Description                                                                                                                                                  |
|--------------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| setState(state) | state     | call it to set the state of the star  .`state` is Boolean                                                                     |
| toggle()   |    no  | call it to toggle the state of the star              |
| ================== | ================ | ============================ |


## License
this project is licensed under the MIT license. (http://opensource.org/licenses/MIT)

the DEMO source code is in the `App.vue`
例子的代码参见 `App.vue`
