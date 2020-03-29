# Iniciando Com Testes Automatizados: Python + Unittes

## Primeiros passos para criação de testes automatizados com a linguagem Python e o framework Unittes

#### Autores: Denini Gabriel - @denini08 && Saulo Barros - @dinosaulo

**Atenção :** Para realizar esse tutorial é necessário possuir instalado em sua máquina o Python3, caso não possuia basta baixa-lo [aqui](https://www.python.org/downloads/) e intala-lo. Também é recomendável possuir conhecimento básico da linguagem.

O Unittest é uma biblicoteca de teste unitário, que foi feito inspirado no JUnit e tem uma abordagem semelhante ao das principais estruturas de teste de unidade das outras linguagens de programação.

O Unittest conta com cários comandos para o Oráculo de casos de testes, como o `assetEqual(X,Y)`, que irá comparar os valores de X e Y, ou como os metodos `setUp()` chamada para antes de casos de teste, assim como o `@before` do Junit e o metodo `tearDown()` chamada para após a execução de casos de teste, assim como o `@after` do Junit. Na documentação da biblioteca presente [aqui](https://docs.python.org/2/library/unittest.html) é possível conferir detalhadamente os métodos disponívels.

Primeiramente vamos criar um arquivo base para nossa funcionalidade. Ela ira fazer uma mediana de três números;
Median.py:
```python
def median (a, b, c):
    med = c
    if (b < c):
        if (a < b):
            med = b
        elif (a < c):
            med = a
    else:
        if (a > b):
            med = b
        elif (a > c):
            med = a

    return med
```

Agora iremos escrever nossos testes. Todos os testes da funcionalidade Median.py ficarão no arquivo MedianTest.py
```python
import unittest
from Median import median

class MedianTestCase(unittest.TestCase):
    def test_median_is_first(self):
        self.assertEqual(2, median(2, 1, 3))

    def test_median_is_last(self):
        self.assertNotEqual(1, median(3, 1, 2))

    # used to skip the test under some justification        
    @unittest.skip('not working') 
    def test_median_is_middle(self):
        self.assertEqual(1, median(1, 2, 3))

if __name__ == '__main__':
    unittest.main()

```