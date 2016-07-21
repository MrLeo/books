```scss

@charset "utf-8";

//开关样式效果：https://gyazo.com/dd1cc3326f77b0dc261b07c3b8f6f3a5
//开关
.l-form.l-form-switch {
    position : relative;
    display  : inline-block;
    
    .l-switch-chk {
        position : absolute;
        top      : 0;
        bottom   : 0;
        left     : 0;
        right    : 0;
        z-index  : 2;
        opacity  : 0;
        width    : 100%;
        height   : 100%;
        margin   : 0;
        padding  : 0;
        cursor   : pointer;
    }
  
    .l-switch-btn {
        position      : relative;
        display       : inline-block;
        border        : 1px solid #ddd;
        padding       : 0 10px;
        border-radius : 3px;
        line-height   : 25px;
        cursor        : pointer;
        overflow      : hidden;
      
        &:before {
            content : attr(data-info) "  " attr(data-info);
        }
      
        &:after {
            content          : "\f00d";
            position         : absolute;
            top              : 0;
            bottom           : 0;
            left             : 0;
            right            : 50%;
            background-color : #ccc;
            text-align       : center;
            color            : #fff;
            font-size        : large;
            font             : normal normal normal 14px/25px FontAwesome;
            transition       : all .4s ease;
        }
    }
  
    .l-switch-chk:checked + .l-switch-btn {
        &:after {
            content          : "\f00c";
            position         : absolute;
            top              : 0;
            bottom           : 0;
            left             : 50%;
            right            : 0;
            background-color : #4cae4c;
            font             : normal normal normal 14px/25px FontAwesome;
        }
    }
}

//二选一开关
.l-form.l-form-switch.l-form-switch2 {
    .l-switch-btn {
        &:before {
            content : attr(data-info) "  " attr(data-info2);
        }
      
        &:after {
            content : "";
        }
    }
  
    .l-switch-chk:checked + .l-switch-btn {
        &:after {
            content : "";
        }
    }
}

//二选一开关2
.l-form.l-form-switch.l-form-switch3 {
    .l-switch-btn {
        &:before {
            content : attr(data-info) "  " attr(data-info2);
        }
      
        &:after {
            content : "";
            background-color : #4cae4c;
        }
    }
  
    .l-switch-chk:checked + .l-switch-btn {
        &:after {
            content : "";
        }
    }
}
```