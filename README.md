# Simulador Asset Light

SPA (single page) em React + TypeScript que replica os cálculos da aba "Simulação" do Excel, usando o prompt como fonte de regras.

## Requisitos

- Node.js 18+

## Rodar local

```bash
npm install
npm run dev
```

Abra o endereço exibido no terminal.

## Build

```bash
npm run build
npm run preview
```

O build gera arquivos estáticos em `dist/`.

## Testes

```bash
npm run test
```

Inclui o Caso base e variações.

## Funcionalidades

- Inputs por seção em cards
- Cálculo automático Ano 1, Ano 2, Ano 3
- Tooltips com fórmulas (no ícone "i")
- Resetar para padrão
- Compartilhar simulação via URL (query param `s` base64 JSON)
- Exportar PDF (Resumo e tabelas por seção)
- Botão "Chamar WhatsApp" configurável por variável de ambiente

## Variável de ambiente

Crie um `.env` a partir de `.env.example`:

```bash
cp .env.example .env
```

Defina:

- `VITE_WHATSAPP_URL`: link do WhatsApp (wa.me ou URL completa)

## Estrutura

- `src/calculator/calculator.ts`: motor de cálculo puro
- `src/calculator/defaults.ts`: valores padrão (defaults da planilha)
- `src/export/pdf.ts`: exportação de PDF
- `src/calculator/calculator.test.ts`: testes automatizados

## Precisão

O motor usa `roundMoney: true` na UI e nos testes para arredondar em centavos ao longo do caminho e reproduzir resultados exibidos no Excel.

Se você quiser operar com precisão máxima (sem arredondar intermediários), chame `calculate(inputs, { roundMoney: false })`.
