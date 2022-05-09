#### 单一比较：
<pre>
html
{{#is_empty resource_list }}
<div>There is no unmanaged VPC to visualse.</div>
{{/is_empty }}

source
Handlebars.registerHelper 'is_empty', ( value, options ) ->

    # is object
    if _.isObject value

        # is empty object {}
        if _.isEmpty value
            options.fn this
        else
            options.inverse this
    else
        options.inverse this

</pre>

#### 两个值的比较：
<pre>
{{#ifCond v1 v2}}
    {{v1}} is equal to {{v2}}
{{else}}
    {{v1}} is not equal to {{v2}}
{{/ifCond}}

Handlebars.registerHelper('ifCond', function(v1, v2, options) {
  if(v1 === v2) {
    return options.fn(this);
  }
  return options.inverse(this);
});
</pre>

#### 重点：
* `options.fn this → true`（返回正确）
* `options.inverse this → false`（返回错误）
