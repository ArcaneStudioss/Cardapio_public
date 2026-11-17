# Arcane Cardápio

SaaS multiempresa de cardápio digital por assinatura. Cada restaurante recebe sua página de pedidos e um painel de gestão.

> Estudo de caso. O código-fonte é privado.

## O que faz
- **Cliente final:** cardápio com fotos e adicionais, sacola, entrega/retirada/mesa (QR), cupom, Pix com valor exato, pagamento online e acompanhamento em tempo real.
- **Dono do restaurante:** quadro de pedidos com som, impressão 80 mm, PDV de balcão com balança, estoque, CMV, cupons, equipe com papéis e relatórios.
- **Atendente de WhatsApp:** o dono escaneia um QR Code e o atendente passa a anotar pedidos usando o cardápio já cadastrado (IA + transcrição de áudio).
- **Integrações:** Mercado Pago, InfinitePay, NFC-e (Focus NFe), iFood e padrão Open Delivery (em homologação), webhooks assinados e API pública v1 documentada com OpenAPI.

## Decisões técnicas
- **Multiempresa:** isolamento por empresa em todas as consultas; credenciais de integração cifradas com AES-256-GCM.
- **Segurança:** preço recalculado no servidor, pagamento só confirmado após consulta ao gateway, tokens guardados só como hash, limites por IP/telefone, uploads validados pela assinatura do arquivo, CSP.
- **Deploy sem queda:** duas réplicas trocadas uma de cada vez, esperando o healthcheck, com rollback automático.
- **Migrações só aditivas**, com teste automatizado que barra `drop`/`delete`.
- **Backup diário** do banco com retenção de 7 dias.

## Stack
Next.js · TypeScript · PostgreSQL · Docker · Traefik · Vitest · Evolution API · Whisper

## Autor
Gabriel · [GitHub](https://github.com/ArcaneStudioss)
