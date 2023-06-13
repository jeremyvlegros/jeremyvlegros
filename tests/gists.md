---
tile : gists
filename : gists.md
---

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





```python
#--------------------------------------------------------------------------------------------------------------------------------------------
ANY = any

def bool_the_parameter_is_a_str_object (_ : ANY = None , bool_print = None) -> bool:
  """
  True if the parameter is an object instantiated from the `str` class # <-- default coloration as default comment

  >>> #> str # str object <-- `docstring > doctest > title > inner comment`
  >>> _= str()
  >>> bool_the_parameter_is_a_str_object(_)
  True

  >>> #> int
  >>> _= 1
  >>> bool_the_parameter_is_a_str_object(_)
  False
  """
  import inspect

  # initialization # Only variables before main code <-- `comment > title 1 > inner comment`

  ## main value    # the return value <-- `comment > title 1 > 1`

  bool_parameter_is_a_str_object: bool = False

  # instance

  if inspect.isclass(_) is False:

    # from str    # instantiated from str class <-- `comment > title 2 > inner comment`

    if isinstance(_, str) is True:

      # str object

      bool_parameter_is_a_str_object = True

  # option print

  if bool_print is True :

    # printing the result

    print(bool_parameter_is_a_str_object)

  # result

  return bool_parameter_is_a_str_object
#--------------------------------------------------------------------------------------------------------------------------------------------

```
