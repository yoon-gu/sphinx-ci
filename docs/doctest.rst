문서에 있는 코드 Snippet들을 자동 테스트
=================================================================

Add Extention
-------------
`conf.py` 파일에 다음과 같이 extension을 추가한다.

.. code-block:: python

	extensions = ['sphinx.ext.doctest']


Test Code
---------

.. testcode::

   1+1         # this will give no output!
   print(2+2)  # this will give output