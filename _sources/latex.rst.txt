한글 LaTeX과 연동하기
=================================================================

LaTeX 설정 옵션 추가
----------------------------------
`conf.py` 파일에 다음과 같이 extension을 추가한다.

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

#. `latex_engine`: LaTeX에서 사용할 엔진, 한글을 위해서는 `xelatex` 으로 변경
#. `latex_elements`: LaTeX 관련 옵션을 저장하는 `Dictionary`.

   * `papersize`: 종이사이즈, `a4paper` 와 `letter` 가 있다.
   * `fontpkg`: 원하는 폰트를 넣을 수 있다.
   * `preamble`: 추가적으로 사용할 LaTeX 패키지를 추가한다.


Sphinx를 이용한 LaTeX Build
----------------------------------

`Makefile`이 존재하는 폴더에 가서 `make latexpdf`를 실행한 후, `pdf` 파일을 확인한다.


LaTeX 예제
----------------------------------

.. math::

   (a + b)^2  &=  (a + b)(a + b) \\
              &=  a^2 + 2ab + b^2 \\
  \int_a^b x^2 dx &= \frac{1}{3} \left(b^3 - a^3\right)
