# 🎳 Bowling Brothers

Sistema completo para gerenciar e acompanhar partidas de boliche entre irmãos.

## 📋 ETAPA 1 - CONCLUÍDA ✅

### Funcionalidades Implementadas

✅ **Estrutura Base**
- HTML5 + CSS3 + JavaScript (arquivo único)
- Tema dark moderno e responsivo
- Tipografia: Poppins
- Ícones SVG temáticos

✅ **Navegação**
- Navbar com seções: Início, Jogadores, Partidas, Estatísticas
- Transições suaves entre seções
- Layout responsivo

✅ **Firebase Firestore**
- Configuração completa do Firebase
- Cache offline habilitado
- Sincronização em tempo real com `onSnapshot`

✅ **CRUD de Jogadores**
- Adicionar jogador
- Editar jogador
- Excluir jogador (com verificação de partidas)
- Listagem com estatísticas (total de partidas, média, melhor score)

✅ **CRUD de Partidas**
- Adicionar partida (jogador, data, pontuação final)
- Editar partida
- Excluir partida
- Listagem ordenada por data

✅ **Dashboard Home**
- Cards com estatísticas gerais:
  - Total de jogadores
  - Total de partidas
  - Média geral
  - Melhor pontuação
- Últimas 6 partidas registradas

✅ **Extras**
- Notificações toast (sucesso, erro, aviso)
- Modais para formulários
- Estados vazios informativos
- Interface totalmente funcional

## 🚀 Como Usar

### 1. Configurar Firebase

**IMPORTANTE**: Antes de usar, você precisa configurar suas credenciais do Firebase.

1. Acesse [Firebase Console](https://console.firebase.google.com/)
2. Crie um novo projeto ou use um existente
3. Ative o Firestore Database
4. Vá em Configurações do Projeto > Suas aplicações
5. Copie as credenciais do Firebase
6. No arquivo `index.html`, substitua as credenciais na linha ~430:

```javascript
const firebaseConfig = {
    apiKey: "SUA_API_KEY",
    authDomain: "SEU_PROJETO.firebaseapp.com",
    projectId: "SEU_PROJETO",
    storageBucket: "SEU_PROJETO.appspot.com",
    messagingSenderId: "SEU_ID",
    appId: "SEU_APP_ID"
};
```

### 2. Abrir o Aplicativo

- Opção 1: Abrir `index.html` diretamente no navegador
- Opção 2: Usar um servidor local (Live Server do VS Code)
- Opção 3: Hospedar no Firebase Hosting

### 3. Usar o Sistema

1. **Adicionar Jogadores**: Vá em "Jogadores" e clique em "Adicionar Jogador"
2. **Registrar Partidas**: Vá em "Partidas" e clique em "Nova Partida"
3. **Ver Estatísticas**: A home mostra estatísticas gerais automaticamente

## � ETAPA 2 - CONCLUÍDA ✅

### Funcionalidades Implementadas

✅ **Sistema de Frames Completo**
- Registro detalhado de cada frame (1-10)
- Entrada de rolls individuais (1ª, 2ª e 3ª bola no frame 10)
- Dois modos: Rápido (só pontuação) ou Detalhado (frame por frame)
- Validação automática de entrada

✅ **Cálculo Automático de Pontuação**
- Algoritmo completo de pontuação de boliche
- Bônus corretos para strikes e spares
- Detecção automática de tipo de frame (strike/spare/open)
- Pontuação em tempo real durante entrada

✅ **Estatísticas Avançadas**
- Média geral de pontuação
- % de strikes, spares e open frames
- Melhor sequência de strikes
- Consistência (desvio padrão)
- Média por frame
- Frequência de primeira bola

✅ **Gráficos Interativos (Chart.js)**
- 📈 **Linha**: Evolução das pontuações por jogador ao longo do tempo
- 📊 **Barras**: Comparação de médias entre jogadores
- 🥧 **Pizza**: Distribuição da primeira bola (0-10 pinos)
- 📉 **Barras**: Média de pinos derrubados por frame

✅ **Filtros e Análises**
- Filtrar por jogador específico
- Filtrar por período (data início/fim)
- Visualização dinâmica das estatísticas
- Atualização em tempo real

✅ **Ranking Completo**
- Tabela com classificação de jogadores
- Ordenação por média de pontuação
- Destaque para 1º, 2º e 3º lugares
- Estatísticas completas (partidas, média, melhor, strikes, spares)

## 📊 Próximas Etapas

### ETAPA 3 - OCR + Extras
- [ ] Upload de imagem de placar
- [ ] OCR com Tesseract.js
- [ ] Filtros por jogador e data
- [ ] Exportar/Importar JSON
- [ ] Dados fictícios de demonstração

## 🛠️ Tecnologias

- **HTML5** - Estrutura
- **CSS3** - Estilização (Dark Theme)
- **JavaScript (ES6+)** - Lógica
- **Firebase Firestore** - Banco de dados em tempo real
- **jQuery** - Manipulação DOM
- **Chart.js 4.4.0** - Gráficos interativos
- **Google Fonts (Poppins)** - Tipografia

## 🎨 Tema Visual

- **Cores principais**:
  - Background: `#0a0a0a`
  - Cards: `#1a1a1a`
  - Primary: `#ff3366` (Rosa/Vermelho)
  - Secondary: `#00d9ff` (Azul Neon)
  - Success: `#00ff88` (Verde)

- **Tipografia**: Poppins (300, 400, 600, 700)
- **Ícones**: SVG inline
- **Layout**: Cards responsivos com grid

## 📱 Responsividade

O layout se adapta automaticamente para:
- Desktop (1400px+)
- Tablet (768px - 1399px)
- Mobile (< 768px)

## 🔒 Cache Offline

O aplicativo funciona offline graças ao cache do Firestore:
- Dados salvos localmente
- Sincronização automática quando online
- Persistência entre sessões

## 📝 Estrutura de Dados (Firestore)

```
players (collection)
├── [playerId]
│   ├── name: string
│   ├── createdAt: timestamp
│   └── updatedAt: timestamp

games (collection)
├── [gameId]
│   ├── playerId: string (ref)
│   ├── date: string (YYYY-MM-DD)
│   ├── finalScore: number (0-300)
│   ├── frames: array (opcional - entrada detalhada)
│   │   └── [
│   │         { frame: 1, rolls: [8, 2], type: "spare" },
│   │         { frame: 2, rolls: [10], type: "strike" },
│   │         { frame: 3, rolls: [7, 1], type: "open" },
│   │         ...
│   │         { frame: 10, rolls: [10, 10, 10], type: "strike" }
│   │       ]
│   ├── createdAt: timestamp
│   └── updatedAt: timestamp
```

## 👥 Autores

**Bowling Brothers Team**
- Projeto criado para gerenciar partidas de boliche entre irmãos

## 📄 Licença

Este projeto é de uso pessoal e educacional.

---

**Status**: ETAPAS 1 e 2 COMPLETAS ✅ | Próximo: ETAPA 3 (OCR + Extras)