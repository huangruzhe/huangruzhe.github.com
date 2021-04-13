---
layout: w
title: Antd 父子组件表单提交
date: 2021-03-01 16:55:27
tags:
---
这两天弄了下父子组件提交的问题，这里整理下。
<!-- more -->
父组件中，引入子组件，对子组件执行React.forwardRef(子组件）来获取传递给它的 ref
=============

配置子组件：<Child ref={React.useRef(null)} />

主要代码如下：
<pre name="code" class="javascript">
const Child = forwardRef(FormItemTimeShedule);
{getFieldDecorator('scheduleList', {
    validateTrigger: ['onBlur'],
    rules: [
        {
            validator(_, value, callback) {
                value.some(item => {
                    const errorMessage = childRef.current.getValidateError(item);
                    if (errorMessage) {
                        callback(errorMessage);
                        return true;
                    }
                    return false;
                });
                callback();
            }
        }
    ],
    initialValue: relativeLinkData
})(<Child ref={React.useRef(null)} {...itemProps}/>)}
</pre>
子组件
=============

定义const FormItemTimeShedule = ( props, childRef) => {....}
使用useImperativeHandle定义暴露给父组件的参数；
  useImperativeHandle(childRef,()=>(
    getValidateError
  }))

//执行校验
<pre name="code" class="javascript">
const getValidateError = item => {
    let msg;
    validators.some(item => {
        if (!item.validator(startTime)) {
            msg = item.message;
            return true;
        }
        return false;
    });
    return msg;
};
</pre>
总结
=============

主要还是卡在forwardRef和useImperativeHandle这里，注意React版本是16以上，我是写的函数式组件。