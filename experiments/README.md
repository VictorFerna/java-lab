## Experiments

Diretório destinado à experimentação de conceitos, ferramentas, bibliotecas integradas dentro do ecossistema **Java**.

Diferentemente dos diretórios exercices, challenges e practice, o experiments é focado na investigação como determinadas funcionalidades funcionam e porque funcionam de tal maneira. 

Exemplos:
- comportamento de tipos;
- referências e objetos;
- Garbage Collector;
- Threads;
- concorrência;
- recursos Java.

O objetivo é experimentar, observar e compreender. Não necessariamente experimentar aplicações completas.

---

## Estrutura do diretório
```text
java-lab/
    └── experiments/
            ├── strings/
            │       └──StringPoolExperiment.java
            │       └── README.md
            ├── memory/
            │       └──GarbageCollectorTest.java
            │       └── README.md
            ├── collections/
            │       └──HashMapExperiment.java
            │       └── README.md
            └── etc...
```
Essa estrutura é apenas um exemplo do modelo do diretório, os nomes dos documentos **md** podem ser renomeados, para que facilitem a sistematização das anotações e modulação dos conteúdos.

Os README.md dentro das pastas de cada experimento será utilizado, como a documentação do experimento, Oque estamos tentando descobrir, o resultado experado, resultado prático, aprendizados. 