# Compilação

* No meio da compilação, temos um código intermediário (IL Code). E ele vai gerar um .exe ou .dll. (Não depende da OS que está sendo usada, é um código abstrato)
* O JIT Compiler pega esse IL Code e transforma para a arquitetura específica da máquina.
* O CLR (Runtime) é como se fosse uma máquina virtual para rodar a aplicação.
* Um transpilador transforma uma linguagem de alto nível para outra de alto nível. Ex.: TypeScript para JavaScript.
  * JavaScript não converte, ele é interpretado direto do código fonte (ou seja, ele possui um interpretador que é capaz de entender o código do jeito que está).
