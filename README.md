# Cubo Mágico 3D

Simulação interativa de um Cubo Mágico em Three.js.

## Controles

| Tecla | Face |
|-------|------|
| `W` / `Shift+W` | Superior |
| `S` / `Shift+S` | Inferior |
| `E` / `Shift+E` | Frontal |
| `F` / `Shift+F` | Traseira |
| `D` / `Shift+D` | Direita |
| `A` / `Shift+A` | Esquerda |

> `Shift` + tecla executa o movimento inverso (sentido antihorário).

##  O que foi implementado
- Cubo 3×3×3 com 27 cubinhos individuais, cada face com cor correta (branco, amarelo, laranja, vermelho, azul, verde)
- Rotação das 6 faces com animação suave (interpolação de 5° por frame)
- Câmera 3D com OrbitControls (arrastar com mouse para orbitar)
- Controles de teclado para todas as 6 faces (normal e inverso com Shift)
- Iluminação com AmbientLight e DirectionalLight
- Contador de movimentos no HUD

### Extras implementados
- Tela de início — ao abrir o jogo, exibe overlay com instruções antes de liberar a interação
- Embaralhamento automático — 20 movimentos aleatórios com animação antes de cada partida
- Botão Resetar — reconstrói o cubo e volta à tela de início
- Detecção de vitória — verifica automaticamente se o cubo foi resolvido após cada movimento
- Gabarito visual — após o embaralhamento, exibe a sequência exata de movimentos para resolver o cubo, com chips coloridos por face
- Histórico de jogadas — registra todos os movimentos feitos pelo jogador em chips coloridos
- Botão Desfazer — reverte o último movimento do jogador sem contar no contador
- Fundo preto com bordas pretas entre os cubinhos para visual clean

## Estrutura do código
O projeto é um único arquivo `index.html` dividido em três partes:
 
### HTML
- **`<style>`** — estilos do HUD, overlays, chips coloridos e responsividade mobile
- **`<canvas #scene>`** — área de renderização Three.js
- **`<section #hud>`** — painel lateral com contador de movimentos, botões, gabarito e histórico
- **`<div #startOverlay>`** — tela de início com tabela de controles
- **`<div #winOverlay>`** — tela de vitória com contador de movimentos
### JavaScript — configuração da cena
- **Scene / Camera / Renderer** — os três pilares do Three.js, câmera perspectiva em (4, 4, 7)
- **OrbitControls** — câmera orbital com damping para navegação com o mouse
- **faceDefinitions** — objeto que mapeia cada tecla (W/S/E/F/D/A) ao eixo, camada e sinal de rotação correspondente
### JavaScript — lógica do cubo
- **`createCube()`** — gera os 27 cubinhos com `BoxGeometry`, materiais individuais por face e arestas pretas com `EdgesGeometry`
- **`rotateFace()`** — agrupa os 9 cubinhos da face num `THREE.Group` temporário e anima a rotação 5° por frame até completar 90°
- **`finishTurn()`** — reancora os cubinhos de volta à cena com `scene.attach()`, atualiza os normais dos stickers e verifica vitória
- **`checkVictory()`** — percorre os stickers de cada face e verifica se todos têm a mesma cor
- **`shuffleCube()`** — executa 20 movimentos aleatórios em sequência e registra cada um no array `scrambleMoves`
- **`showSolutionPanel()`** — renderiza o gabarito como chips HTML coloridos por face (sequência inversa do embaralhamento)
- **Loop de animação** — `requestAnimationFrame` chamando `animateTurn()` e `controls.update()` a cada frame
