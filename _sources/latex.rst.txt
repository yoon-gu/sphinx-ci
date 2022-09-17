한글 LaTeX과 연동하기
=================================================================

* 참조 링크: https://www.sphinx-doc.org/en/master/latex.html

:index:`LaTeX` 설정 옵션 추가
----------------------------------
:file:`conf.py` 파일에 다음과 같이 extension을 추가한다.

.. code-block:: python

   latex_engine = 'xelatex'
   latex_elements = {
      'papersize':'a4paper',
       'fontpkg': r'''
   \setmainfont[Kerning=On,Mapping=tex-text]{나눔명조}
   \setsansfont[Kerning=On,Mapping=tex-text]{나눔명조}
   \setmonofont{JetBrains Mono}
   ''',
       'preamble': r'''
   \usepackage{kotex}
   '''
   }
   latex_show_urls = 'footnote'

#. :code:`latex_engine`: LaTeX에서 사용할 엔진, 한글을 위해서는 :code:`xelatex` 으로 변경
#. :code:`latex_elements`: LaTeX 관련 옵션을 저장하는 :code:`Dictionary`.

   * :code:`papersize`: 종이사이즈, :code:`a4paper` 와 :code:`letter` 가 있다.
   * :code:`fontpkg`: 원하는 폰트를 넣을 수 있다.
   * :code:`preamble`: 추가적으로 사용할 LaTeX 패키지를 추가한다.


Sphinx를 이용한 LaTeX Build
----------------------------------

:code:`Makefile` 이 존재하는 폴더에 가서 :code:`$ make latexpdf` 를 실행한 후, :code:`pdf` 파일을 확인한다.


LaTeX 예제
----------------------------------

수식 예제
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. math::

   (a + b)^2  &=  (a + b)(a + b) \\
              &=  a^2 + 2ab + b^2 \\
  \int_a^b x^2 dx &= \frac{1}{3} \left(b^3 - a^3\right)

Table 예제 1
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. list-table:: List를 활용하여 테이블 만들기
   :widths: 25 25 50
   :header-rows: 1

   * - Heading row 1, column 1
     - Heading row 1, column 2
     - Heading row 1, column 3
   * - Row 1, column 1
     -
     - Row 1, column 3
   * - Row 2, column 1
     - Row 2, column 2
     - Row 2, column 3

.. code-block:: rst

   .. list-table:: List를 활용하여 테이블 만들기
      :widths: 25 25 50
      :header-rows: 1

      * - Heading row 1, column 1
        - Heading row 1, column 2
        - Heading row 1, column 3
      * - Row 1, column 1
        -
        - Row 1, column 3
      * - Row 2, column 1
        - Row 2, column 2
        - Row 2, column 3

Table 예제 2
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: rst

   +------------+------------+-----------+
   | Header 1   | Header 2   | Header 3  |
   +============+============+===========+
   | body row 1 | column 2   | column 3  |
   +------------+------------+-----------+
   | body row 2 | Cells may span columns.|
   +------------+------------+-----------+
   | body row 3 | Cells may  | - Cells   |
   +------------+ span rows. | - contain |
   | body row 4 |            | - blocks. |
   +------------+------------+-----------+

+------------+------------+-----------+
| Header 1   | Header 2   | Header 3  |
+============+============+===========+
| body row 1 | column 2   | column 3  |
+------------+------------+-----------+
| body row 2 | Cells may span columns.|
+------------+------------+-----------+
| body row 3 | Cells may  | - Cells   |
+------------+ span rows. | - contain |
| body row 4 |            | - blocks. |
+------------+------------+-----------+