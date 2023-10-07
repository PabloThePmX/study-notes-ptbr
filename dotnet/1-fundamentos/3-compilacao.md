# Compilação

### IL Code
* Durante a compilação, teremos um código intermediário (IL Code), com ele vai ser gerarado o .exe ou a .dll. 
  * O IL Code não depende da OS que está sendo usada, pois é um código abstrato

### JIT e CLR
* O **JIT Compiler** pega esse IL Code e transforma para a arquitetura específica da máquina.
* O **CLR (Runtime)** é como se fosse uma máquina virtual para rodar a aplicação.
  
### Transpilador
* Um transpilador transforma uma linguagem de alto nível para outra de alto nível. Ex.: TypeScript para JavaScript.
  * JavaScript não converte, ele é interpretado direto do código fonte (ou seja, ele possui um interpretador que é capaz de entender o código do jeito que está).
