<!--
Projeto de Recurso de Linguagens de Programação II 2025/2026 (c) by Nuno Fachada

Projeto de Recurso de Linguagens de Programação II 2025/2026 is licensed under a
Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License.

You should have received a copy of the license along with this
work. If not, see <http://creativecommons.org/licenses/by-nc-sa/4.0/>.
-->

# Projeto de Recurso de Linguagens de Programação II 2025/2026

## Descrição do problema

Os grupos devem implementar o jogo de tabuleiro "Linces e Coelhos" para dois
jogadores na forma de um projeto Unity (6000.0.x) em C# 9.0.

A lógica, possíveis movimentos, regras, estado do tabuleiro e do jogo (o chamado
**modelo**), devem ser completamente independentes do Unity. Ou seja, este
modelo **não pode** fazer `using` de _namespaces_ do Unity ou de qualquer outra
biblioteca não presente no C# 9.0.

O [Model-View-Controller (MVC)][MVC] *design pattern* é necessário para a
realização deste projeto. Por exemplo, [neste projeto Unity][ia-simplexity], o
modelo é completamente independente do Unity, sendo trivial implementar uma
versão em consola.

O exemplo [MVCExample] e o [respetivo vídeo de desenvolvimento][MVCVideo] são
essenciais para a compreensão do que é necessário fazer neste projeto. Podem
ignorar a parte dos módulos Git, pois neste projeto vao implementar apenas o
jogo em Unity. No entanto, tenham atenção que no _live coding_ (ver em baixo)
pode ser pedida uma implementação em consola, que só funcionará se o modelo
estiver de facto bem separado do resto.

O objetivo principal deste projeto é a implementação de uma aplicação com uma
arquitetura bem pensada e bem desenhada, que permita facilmente alterar as
regras base do jogo bem como o respetivo tabuleiro. Obviamente que o jogo deve
funcionar corretamente, mas isso por si só não serve de nada se os
[requisitos técnicos obrigatórios](#requisitos-técnicos-obrigatórios),
nomeadamente a nível de arquitetura, não tiverem sido cumpridos.

## Linces e Coelhos <img src="lincesecoelhos.png" width="100px" align="left" />

O jogo "Linces e Coelhos" é um jogo de tabuleiro para dois jogadores. Um jogador
joga com os linces, o outro joga com os coelhos.

As regras do jogo estão disponíveis em vídeo no Moodle. Para a versão a
entregar, devem ter em conta os seguintes parâmetros:

- O tabuleiro apresentado no vídeo com os **3** linces colocados nas posições
  indicadas no vídeo.
- Devem existir **15** coelhos a serem colocados no tabuleiro.
- Os linces ganham se comerem **5** coelhos.
- Os coelhos ganham se bloquearem os movimentos dos linces.
- O jogo termina em empate caso o mesmo tabuleiro se repita **3** vezes nas
  últimas **6** jogadas.

Estes parâmetros, bem como a topologia de tabuleiro devem ser facilmente
alteráveis, e o _live coding_ consistir em fazer exatamente isso.

## Requisitos da aplicação

### Requisitos técnicos obrigatórios

Os seguintes requisitos são obrigatórios. Caso não sejam tidos em conta, a nota
do projeto é zero.

#### Arquitetura de classes e _patterns_

O projeto deve obedecer aos princípios [SOLID], bem como aos princípios gerais
de design de classes. Devem usar o [MVC] *pattern* para organizar o código (bem
como outros _patterns_ que considerem relevantes), e o código do modelo **não
pode** fazer `using` de _namespaces_ do Unity ou de qualquer outra biblioteca
não presente no C# 9.0. Devem ainda balancear esta abordagem com o princípio
[KISS], evitando complexidade desnecessária.

#### Funcionamento da aplicação

A nível de jogabilidade/interação:

* O jogo tem de funcionar corretamente.
* A aplicação deve ter um menu inicial com as opções "Play", "Authors" e "Quit".
* A UI do jogo deve ser intuitiva, e as peças / movimentos possíveis do jogador
  atual devem estar claramente identificados. Devem testar o jogo com familiares
  ou amigos para determinar se os mesmos conseguem jogar sem explicações (além
  das regras).
* Durante o jogo, devem existir opções para voltar ao menu principal e para
  sair imediatamente da aplicação (tanto no editor, como na _build_), e as
  mesmas devem estar claramente indicadas no UI.

### Sugestões de implementação

- Criem primeiro o jogo em papel, joguem-no umas quantas vezes, e certifiquem-se
  que entendem perfeitamente as regras do mesmo!
- A nível do código, pensem no tabuleiro do jogo como um conjunto de
  **posições** ligadas por um conjunto de **ligações**. Tanto as **posições**
  como as **ligações** devem ser facilmente parameterizáveis (em código, ou
  possivelmente lidas de um ficheiro de configuração que vocês definam).
- As **posições** podem estar vazias, ter um lince, ter um coelho, mas nunca
  mais do que uma peça ao mesmo tempo.
- A captura de uma peça só pode ser feita saltando por cima da peça **em linha
  reta**. Ou seja, apesar as **posições** no tabuleiro serem arbitrárias, a
  geometria é crucial para a captura de peças.

## Avaliação, discussão e _live coding_

A avaliação, discussão e _live coding_ serão realizadas no dia **30 de janeiro
da parte da tarde, a partir das 14h00**. Devem reservar a tarde toda para esta
componente.

A avaliação será feita com cada grupo, analisando o jogo, o código, e as
restantes componentes de avaliação. Serão feitas perguntas a cada elemento do
grupo sobre o código, sendo as respostas dadas tidas em conta como parte da
discussão.

Por fim, os estudantes terão uma avaliação final de _live coding_, que também
contará para o processo de discussão. Neste _live coding_ será pedido aos
estudantes que alterem uma das componentes ou regras do jogo, como por exemplo:

- Alterar o número de linces iniciais ou coelhos que se podem colocar durante o
  jogo.
- Limitar o número de passos que cada lince pode dar durante o jogo todo.
- Alterar o tabuleiro de jogo segundo um desenho que vos será dado na altura.
- Acrescentar um "super-lince" que possa capturar mais do que um coelho de cada
  vez, ou furar um bloqueio uma única vez, ou outra coisa semelhante.
- Acrescentar um "super-coelho" que bloqueie um lince simplesmente estando numa
  casa adjacente, ou até que consiga matar um lince (saltando por cima dele).
- Permitir aos coelhos serem colocados dois de cada vez.
- Converter o jogo em lince vs. lince (em que os linces de diferentes jogadores
  se podem capturar uns aos outros).
- Implementar uma versão em consola, reutilizando **sem alterar** o código do
  **modelo** do MVC.
- Um conjunto dos pontos anteriores ou algo parecido ou diferente.

Para que consigam fazer estas ou outras alterações, é essencial que o vosso
projeto siga as melhores práticas e seja facilmente alterável e extensível. Por
exemplo, para conseguirem parameterizar diferentes tabuleiros, o uso de _arrays_
é péssima ideia.

## Objetivos e critério de avaliação

Este projeto tem os seguintes objetivos:

* **O1** - O projeto deve funcionar tal como indicado na secção
  [Funcionamento da aplicação](#funcionamento-da-aplicação).
* **O2** - Projeto deve ser implementado segundo o que está definido na secção
  [Arquitetura de classes e _patterns_](#arquitetura-de-classes-e-patterns).
  Além disso, o projeto não deve ter código "morto", que não faz nada, como por
  exemplo variáveis, propriedades ou métodos nunca usados.
* **O3** - Código devidamente indentado, comentado e documentado. Documentação
  deve ser feita com [comentários de documentação XML][XML].
* **O4** - Repositório Git deve refletir boa utilização do mesmo, com
  *commits* de todos os elementos do grupo e mensagens de *commit* que sigam
  as melhores práticas para o efeito (como indicado
  [aqui](https://chris.beams.io/posts/git-commit/),
  [aqui](https://gist.github.com/robertpainsi/b632364184e70900af4ab688decf6f53),
  [aqui](https://github.com/erlang/otp/wiki/writing-good-commit-messages) e
  [aqui](https://stackoverflow.com/questions/2290016/git-commit-messages-50-72-formatting)).
  Quaisquer *assets* binários, tais como imagens, devem ser integrados
  no repositório em modo Git LFS (atenção que este último ponto é **muito
  importante**).
* **O5** - Relatório em formato [Markdown] (ficheiro `README.md`),
  organizado da seguinte forma:
  * Título do projeto.
  * Autoria:
    * Nome dos autores (primeiro e último) e respetivos números de aluno.
    * Informação de quem fez o quê no projeto. Esta informação é
      **obrigatória** e deve refletir os *commits* feitos no Git.
  * Arquitetura da solução:
    * Descrição da solução, com breve explicação de como o programa foi
      organizado, indicação dos *design patterns* utilizados e a razão do
      seu uso, bem como dos algoritmos implementados (e.g., para procura de
      peças jogáveis, etc).
    * Um diagrama UML de classes simples (i.e., sem indicação dos
      membros da classe) descrevendo a estrutura de classes (**obrigatório**).
  * Referências, incluindo trocas de ideias com colegas, sugestões dadas por IAs
    generativas (e.g., ChatGPT), código aberto reutilizado (e.g., do
    StackOverflow) e bibliotecas de terceiros utilizadas. Devem ser o mais
    detalhados possível.
  * **Nota:** o relatório deve ser simples e breve, com informação mínima e
    suficiente para que seja possível ter uma boa ideia do que foi feito.
    Atenção aos erros ortográficos e à correta formatação [Markdown], pois
    ambos serão tidos em conta na nota final.

O projeto tem um peso de 10 valores na nota final da disciplina e será avaliado
de forma qualitativa. Isto significa que todos os objetivos têm de ser
parcialmente ou totalmente cumpridos. A cada objetivo, O1 a O5, será atribuída
uma nota entre 0 e 1. A nota do projeto será dada pela seguinte fórmula:

$N = 10 \times O_1 \times O_2 \times O_3 \times O_4 \times O_5 \times D$

Em que $D$ corresponde à nota da discussão, _live coding_ e percentagem
equitativa de realização do projeto, também entre 0 e 1. Isto significa que se os alunos
ignorarem completamente um dos objetivos, não tenham feito nada no projeto ou
não comparecerem na discussão / _live coding_, a nota final será zero.

## Entrega

O projeto é entregue de forma automática através do GitHub. Mais concretamente,
o repositório do projeto será automaticamente clonado às **23h00 de 29 de
janeiro de 2026**. Certifiquem-se de que a aplicação está funcional e que todos
os requisitos foram cumpridos, caso contrário o projeto não será avaliado.

O repositório deve ter:

* Projeto de Unity 6000.0.x funcional.
* Ficheiros `.gitignore` e `.gitattributes` adequados para o projeto em questão.
* Ficheiro `README.md` contendo o relatório do projeto em formato [Markdown].
* Ficheiros de imagens, contendo o diagrama UML de classes e outras figuras
  que considerem úteis. Estes ficheiros devem ser incluídos no repositório em
  modo Git LFS. Em alternativa, o UML e outros diagramas que considerem úteis
  podem ser feitos em [Mermaid].

Em nenhuma circunstância o repositório pode ter _builds_ ou outros ficheiros
temporários dos projetos, do Visual Studio e do Unity, que são automaticamente
ignorados se usarem um `.gitignore` apropriado.

## Honestidade académica

Nesta disciplina, espera-se que cada aluno siga os mais altos padrões de
honestidade académica. Isto significa que cada ideia que não seja do
aluno deve ser claramente indicada, com devida referência ao respetivo
autor. O não cumprimento desta regra constitui plágio.

O plágio inclui a utilização de ideias, código ou conjuntos de soluções
de outros alunos ou indivíduos, ou quaisquer outras fontes para além
dos textos de apoio à disciplina, sem dar o respetivo crédito a essas
fontes. Os alunos são encorajados a discutir os problemas com outros
alunos e devem mencionar essa discussão quando submetem os projetos.
Essa menção **não** influenciará a nota. Os alunos não deverão, no
entanto, copiar códigos, documentação e relatórios de outros alunos, ou dar os
seus próprios códigos, documentação e relatórios a outros em qualquer
circunstância. De facto, não devem sequer deixar códigos, documentação e
relatórios em computadores de uso partilhado.

**Sobre IAs generativas (e.g. ChatGPT):** podem usar este tipo de ferramentas
para esclarecer dúvidas, ou até para obterem uma ou outra sugestão de código,
desde de que as ideias e organização geral do projeto sejam originais. Código
completamente fornecido por uma IA generativa será facilmente detetável pelas
ferramentas de deteção de plágio, pelo que sugerimos muito cuidado no uso deste
tipo de ferramentas. De qualquer forma, todo o código gerado através de IA
(parcialmente ou totalmente) deve ser indicado em forma de comentário e nas
referências do relatório.

Nesta disciplina, a desonestidade académica é considerada fraude, com
todas as consequências legais que daí advêm. Qualquer fraude terá como
consequência imediata a anulação dos projetos de todos os alunos envolvidos
(incluindo os que possibilitaram a ocorrência). Qualquer suspeita de
desonestidade académica será relatada aos órgãos superiores da escola
para possível instauração de um processo disciplinar. Este poderá
resultar em reprovação à disciplina, reprovação de ano ou mesmo suspensão
temporária ou definitiva da ULHT.

*Texto adaptado da disciplina de [Algoritmos e Estruturas de Dados][aed] do
[Instituto Superior Técnico][ist]*

## Referências

* \[1\] Whitaker, R. B. (2022). **The C# Player's Guide** (5th Edition).
  Starbound Software.
* \[2\] Albahari, J., & Johannsen, E. (2020). **C# 8.0 in a Nutshell**. O’Reilly
  Media.
* \[3\] Freeman, E., Robson, E., Bates, B., & Sierra, K. (2020). **Head First
  Design Patterns** (2nd edition). O'Reilly Media.
* \[4\] Dorsey, T. (2017). **Doing Visual Studio and .NET Code Documentation
  Right**. Visual Studio Magazine. Retrieved from
  <https://visualstudiomagazine.com/articles/2017/02/21/vs-dotnet-code-documentation-tools-roundup.aspx>.

## Licenças

Este enunciado é disponibilizado através da licença [CC BY-NC-SA 4.0].

## Metadados

* Autor: [Nuno Fachada]
* Curso: [Licenciatura em Videojogos][lamv]
* Instituição: [Universidade Lusófona - Centro Universitário de Lisboa][ULHT]

[CC BY-NC-SA 4.0]:https://creativecommons.org/licenses/by-nc-sa/4.0/
[lamv]:https://www.ulusofona.pt/licenciatura/videojogos
[Nuno Fachada]:https://github.com/fakenmc
[ULHT]:https://www.ulusofona.pt/
[aed]:https://fenix.tecnico.ulisboa.pt/disciplinas/AED-2/2009-2010/2-semestre/honestidade-academica
[ist]:https://tecnico.ulisboa.pt/pt/
[Markdown]:https://guides.github.com/features/mastering-markdown/
[KISS]:https://en.wikipedia.org/wiki/KISS_principle
[XML]:https://docs.microsoft.com/dotnet/csharp/codedoc
[SOLID]:https://en.wikipedia.org/wiki/SOLID
[MVC]:https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller
[ia-simplexity]:https://github.com/VideojogosLusofona/color-shape-links-ai-competition
[MVCExample]:https://github.com/VideojogosLusofona/MVCExample.git
[MVCVideo]:https://www.youtube.com/watch?v=_z_iRUjmvzE
[Mermaid]:https://mermaid.js.org/
