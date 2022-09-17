문서에 있는 코드 Snippet들을 자동 테스트
=================================================================

* 참조 링크 1: https://www.sphinx-doc.org/en/master/usage/extensions/doctest.html
* 참조 링크 2: https://thomas-cokelaer.info/tutorials/sphinx/doctest.html

Add Extention
-------------
:file:`conf.py` 파일에 다음과 같이 extension을 추가한다.

.. code-block:: python

	extensions = ['sphinx.ext.doctest']


Test Code
---------

.. doctest::

   >>> print("Hello")
   Hello

.. testcode::

   1+1         # this will give no output!
   print(2+2)  # this will give output

출력값은 다음과 같습니다.

.. testoutput::

   4

위의 코드 내용을 다음과 같은 :code:`rst` 작성을 하게 되면 :code:`$ make doctest` 를 통해 테스트를 진행할 수 있습니다.

.. code-block:: rst

   .. doctest::

      >>> print("Hello")
      Hello

   .. testcode::

      1+1         # this will give no output!
      print(2+2)  # this will give output

   출력값은 다음과 같습니다.

   .. testoutput::

      4

테스트를 실행하면 다음과 같은 출력이 나옵니다.

.. code-block:: rst

   running tests...

   Document: doctest
   -----------------
   1 items passed all tests:
      2 tests in default
   2 tests in 1 items.
   2 passed and 0 failed.
   Test passed.

   Doctest summary
   ===============
       2 tests
       0 failures in tests
       0 failures in setup code
       0 failures in cleanup code
   빌드 성공.

테스트 실패 사례를 고의로 만들기 위해서 다음의 상황을 생각해봅니다.

.. code-block:: rst

   .. testcode::

      print(2+2)

   출력값은 다음과 같습니다.

   .. testoutput::

      5

그러면 다음과 같은 결과가 나옵니다.

.. code-block:: rst

	running tests...

	Document: doctest
	-----------------
	**********************************************************************
	File "doctest.rst", line 47, in default
	Failed example:
	    print(2+2)
	Expected:
	    5
	Got:
	    4
	**********************************************************************
	1 items had failures:
	   1 of   2 in default
	2 tests in 1 items.
	1 passed and 1 failed.
	***Test Failed*** 1 failures.

	Doctest summary
	===============
	    2 tests
	    1 failure in tests
	    0 failures in setup code
	    0 failures in cleanup code
	빌드 완료했으나 문제점 발견.
