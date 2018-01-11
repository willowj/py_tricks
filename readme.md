python trick packages

[trick codes](/trick_codes.md )



### [pdir2](https://github.com/laike9m/pdir2#pdir2-pretty-dir-printing-with-joy)

- Pretty dir()


-  ![](https://github.com/laike9m/pdir2/raw/master/images/presentation_v2.gif)

- 可以设置 ipython auto import 

  > [add  a startup file(.py) to ~/.ipython/profile_default/startup/](https://stackoverflow.com/questions/11124578/automatically-import-modules-when-entering-the-python-or-ipython-interpreter)

  ​

### [json-sempai]( https://github.com/kragniz/json-sempai )

​	Use JSON files as if they are python modules 

​	导入json 文件作为一个包使用

- > tester.json
  >
  > ```
  > {
  >     "hello": "world",
  >     "this": {
  >         "can": {
  >             "be": "nested"
  >         }
  >     }
  > }
  > ```
  >
  > Now import jsonsempai and your json file!
  >
  > ```python
  > >>> from jsonsempai import magic
  > >>> import tester
  > >>> tester
  > <module 'tester' from 'tester.json'>
  > >>> tester.hello
  > u'world'
  > >>> tester.this.can.be
  > u'nested'
  > >>>
  > ```

