문서에 있는 코드 Snippet들을 자동으로 실행 후 출력값 자동 표시
=================================================================

* 참조 링크 1: https://sphinx-exec-code.readthedocs.io/en/latest/index.html
* 참조 링크 2: https://sphinx-gallery.github.io/stable/auto_examples/plot_3_capture_repr.html
   * 이거는 그림까지 링크가 되는 것 같습니다.

간단히 아래와 같이 입력하면 저절로 출력값이 채워지는 편리한 기능입니다. 하지만 이미지같은 것들도 되는지는 알 수 없습니다.

.. code-block:: rst

   .. exec_code::

      print('Easy!')

위의 코드가 Parsing된 후 결과는 아래와 같습니다.

.. exec_code::

   print('Easy!')

:code:`print` 를 2번 하면 출력값도 2번 나옵니다.

.. exec_code::
   :linenos:

   print('Easy!')
   print(5+3)
