# Uso de Inteligência Artificial

## Modelos utilizados

ChatGPT GPT-5.5 (via chatgpt.com)  geração da base do código e ajustes principais

## Detalhamento por etapa
 
### 1. Geração inicial do projeto
**Modelo:** ChatGPT GPT-5.5  
 
**Prompt utilizado:**
 Crie um projeto completo de Cubo Mágico 3D em um único arquivo `index.html` auto-contido, sem dependências externas além de Three.js via CDN. Cubo 3×3×3 com 27 cubinhos individuais, rotação de 6 faces com animação suave via THREE.Group, câmera com OrbitControls r128, controles de teclado (W/S/E/F/D/A), iluminação com AmbientLight e DirectionalLight, contador de movimentos, botão embaralhar com 20 movimentos aleatórios, detecção de vitória e gabarito por inversão da sequência de embaralhamento.
 
### 2. Adição de tela de início, gabarito visual e histórico
**Modelo:** ChatGPT GPT-5.5  

**Prompt utilizado:**
 Faça as seguintes correções e adições no arquivo index.html atual. As bindings de teclado já foram alteradas e NÃO devem ser modificadas. Adicione: tela de início com overlay antes de jogar, fluxo padronizado (sempre embaralhar antes de jogar), painel "Ver Gabarito" colapsável com chips coloridos por face (cada face com sua cor: branco, amarelo, azul, verde, vermelho, laranja), histórico de jogadas do jogador com chips na mesma estética e botão desfazer que reverte o último movimento. Fundo preto puro (#000000).

### 3. Correção do bug no gabarito
**Modelo:** ChatGPT GPT-5.5  
**Problema:** O gabarito exibia os movimentos com o apóstrofo invertido e a lógica de inversão estava incorreta para faces com `sign: -1`. 
**Prompt utilizado:**
 Há um bug no gabarito: a lógica do apóstrofo está trocada na função showSolutionPanel. Se o embaralhamento girou normal (inverse=false), o gabarito deve mostrar o inverso com apóstrofo. Se girou inverso (inverse=true), o gabarito mostra normal sem apóstrofo. Corrija apenas a linha do .map() sem alterar mais nada.
 
### 4. Revisão da documentação
**Modelo:** ChatGPT GPT-5.5   
Utilizado para revisar e formatar a documentação do projeto, corrigindo estrutura, clareza e organização dos textos gerados pela equipe.
## Considerações

O uso de IA foi supervisionado em todas as etapas. Cada código gerado foi revisado e testado no navegador antes de ser incorporado ao projeto. Os bugs foram analisados pelo grupo antes de ser enviados à IA para correção, garantindo que todos os integrantes compreendessem as soluções aplicadas.
