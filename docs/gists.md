---
tile : gists
filename : gists.md
---

with Markdown

```xml
<snippet>
	<content>
		<![CDATA[#--------------------------------------------------------------------------------------------------------------------------------------------
def ${1:TYPE}_${2:FUNCTION_NAME}_for (${3:ARGUMENTS}) -> ${1:TYPE}:
  """
  # description :

  >>> #>
  >>> tuple_arguments = (${3:ARGUMENTS}:=)
  >>> ${1:TYPE}_${2:FUNCTION_NAME}_for (*tuple_arguments)
  """

  # initialization

  ## main value

  ${1:TYPE}_${2:FUNCTION_NAME} =

  # result

  return ${1:TYPE}_${2:FUNCTION_NAME}

]]>
	</content>
	<!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
	<tabTrigger>def</tabTrigger>
	<!-- Optional: Set a scope to limit where the snippet will trigger -->
  <scope>source.python - meta.function.parameters - meta.function-call - meta.statement - meta.mapping - meta.sequence - meta.set - comment - string</scope>
</snippet>
```
with Rouge & Jekyll

{% highlight xml %}
<snippet>
	<content>
		<![CDATA[#--------------------------------------------------------------------------------------------------------------------------------------------
def ${1:TYPE}_${2:FUNCTION_NAME}_for (${3:ARGUMENTS}) -> ${1:TYPE}:
  """
  # description :

  >>> #>
  >>> tuple_arguments = (${3:ARGUMENTS}:=)
  >>> ${1:TYPE}_${2:FUNCTION_NAME}_for (*tuple_arguments)
  """

  # initialization

  ## main value

  ${1:TYPE}_${2:FUNCTION_NAME} =

  # result

  return ${1:TYPE}_${2:FUNCTION_NAME}

]]>
	</content>
	<!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
	<tabTrigger>def</tabTrigger>
	<!-- Optional: Set a scope to limit where the snippet will trigger -->
  <scope>source.python - meta.function.parameters - meta.function-call - meta.statement - meta.mapping - meta.sequence - meta.set - comment - string</scope>
</snippet>
{% endhighlight %}
