# BlueAqua 💙☁️ — Bot de vendas da Blues Nuvem Store
Criador: @dnl_losys • Node.js + discord.js v14 • SQLite persistente • Pix por chave (BR Code), sem API bancária.

## Instalação
1. Node 18+ (ideal 22). `npm install`
2. Copie `.env.example` para `.env` e preencha `DISCORD_TOKEN` e `GUILD_ID` (no Replit: aba **Secrets**). Nunca publique o token.
3. No Discord Developer Portal → Bot, ative **Message Content Intent** e **Server Members Intent**.
4. Convite do bot com escopos `bot` + `applications.commands` e permissões: Ver canais, Enviar mensagens, Gerenciar canais, Anexar arquivos, Inserir links, Ler histórico, Adicionar reações.
5. `npm start` — os 11 comandos slash são registrados automaticamente na inicialização (com `GUILD_ID` aparecem na hora).
6. `npm test` roda os testes da lógica (Pix, calculadora, cupons, pedidos, estoque).

## Configuração inicial (como administrador)
1. `/config cargo` (administrador e atendente) e `/config canal` (vendas, calculadora, proofs, entregas, logs).
2. `/config categoria` (opcional): categorias do Discord onde os tickets serão criados.
3. `/painel` → **Configurar Pix** (tipo, chave, nome e cidade) e **Preços e taxas** — os valores padrão são só EXEMPLOS, ajuste os seus.
4. `/cad adicionar` produtos de MM2/FTF; `/estoque` para ajustar.
5. `/painel` → **Publicar vitrine** no canal de vendas.

## Fluxo
Vitrine → produto/método → quantidade + cupom (modal) → resumo → **pedido** + canal privado + painel + QR/Copia e Cola → cliente envia imagem do comprovante → status AGUARDANDO CONFERÊNCIA + envio ao canal de proofs → equipe confere o recebimento real e **aprova** (com confirmação) → entrega registrada → ENTREGUE (e publicada no canal de entregas).

## Comandos
`/painel` `/admin` (cupons, publicar entrega) `/cad` `/estoque` `/config` `/pedido` `/calculadora` `/precos` `/ticket` `/proof` `/relatorio`

## Importante
- **Não há confirmação automática de pagamento.** Comprovante em imagem NÃO confirma nada; só a equipe aprova depois de ver o dinheiro na conta.
- OCR/IA **não está implementado**: o campo "valor identificado" aparece como conferência manual.
- Dados ficam em `data/blueaqua.sqlite` (faça backup). Em hospedagens com disco efêmero, use armazenamento persistente.
- Links de imagens do Discord podem expirar com o tempo; o histórico textual do pedido e as transcrições ficam no banco.
