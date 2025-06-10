# Caminhos em Mapas com Penalidade de Mudança de Direção

Este projeto resolve o problema de encontrar caminhos mínimos entre portos em um mapa, considerando penalidades para mudança de direção, utilizando o algoritmo de Dijkstra modificado. O programa lê um mapa de texto, identifica portos e caminhos bloqueados, gera um grafo direcionado ponderado e calcula o menor custo para percorrer todos os portos.

---

## Estrutura do Projeto

```
src/
 ├── App.java
 ├── Dijkstra.java
 ├── Direcoes.java
 ├── Edge.java
 ├── EdgeWeightedDigraph.java
 ├── EdgeWeightedGraph.java
 ├── In.java
 ├── IndexMinHeap.java
 ├── Nodo.java
 ├── CasosTeste/
 │    └── mapas/
 └── Arestas.txt
```

- **App.java**: Classe principal, responsável por ler o mapa, gerar portos e arestas, criar o grafo e calcular o custo mínimo do ciclo entre os portos usando Dijkstra.
- **Dijkstra.java**: Implementação do algoritmo de Dijkstra com penalidade para mudança de direção.
- **Direcoes.java**: Enumeração das possíveis direções (NORTE, SUL, LESTE, OESTE, INICIAL).
- **Edge.java**: Representa uma aresta no grafo, com vértices, peso e cor.
- **EdgeWeightedDigraph.java**: Grafo direcionado e ponderado, utilizado para os caminhos.
- **EdgeWeightedGraph.java**: Implementação genérica de grafos ponderados.
- **In.java**: Utilitário para leitura de arquivos.
- **IndexMinHeap.java**: Heap de prioridade por índices, otimiza o Dijkstra.
- **Nodo.java**: Classe utilitária para coordenadas no mapa.
- **CasosTeste/mapas/**: Pasta para mapas de teste utilizados como entrada.
- **Arestas.txt**: Arquivo gerado com as arestas do grafo para uso posterior.

---

## Funcionamento

1. **Leitura do Mapa**
   - O mapa é lido a partir de um arquivo texto (`mapaXXX.txt`), onde:
     - `*` representa obstáculos (impassável).
     - `.` representa caminho livre.
     - Letras (ex: `A`, `B`, ...) representam portos.

2. **Geração do Grafo**
   - Cada célula acessível vira um vértice (`i x j`).
   - São criadas arestas entre vizinhos não bloqueados (peso 1).
   - Mudanças de direção recebem penalidade extra (peso 2 adicional).

3. **Cálculo dos Caminhos**
   - Para cada par de portos, calcula-se o menor caminho considerando penalidades.
   - O programa tenta encontrar um ciclo que passe por todos os portos, somando o custo total.

4. **Saída**
   - Exibe caminhos mínimos entre os portos e o custo total do ciclo.
   - Arquivo `Arestas.txt` é gerado para persistência do grafo.

---

## Exemplo de Mapa de Entrada

```
5 5
A...B
.***.
.C.D.
.***.
E...F
```

## Como Executar

1. Compile o projeto:
   ```sh
   javac src/*.java
   ```
2. Execute o programa:
   ```sh
   java -cp src App
   ```

- **Atenção:** Ajuste os caminhos dos arquivos de entrada no início do `App.java` conforme a organização das pastas no seu ambiente.

---

## Dependências

- Java 8+
- Nenhuma biblioteca externa necessária.

---

## Customização

- Adicione novos mapas na pasta `src/CasosTeste/mapas/` para testar diferentes configurações.
- Modifique os pesos das penalidades alterando o valor nas linhas correspondentes do algoritmo de Dijkstra.

---

## Autoria

Projeto acadêmico para estudo de algoritmos de caminhos mínimos com penalidade de direção.

— Julia Yume Kriedte
—  Mariana Adam dos Anjos
```
