# Arquitetura de um Sistema de Venda de Ingressos em Alta Demanda

## 📌 Sobre o projeto

Este projeto apresenta uma proposta de arquitetura para um sistema de venda de ingressos para um evento de grande porte, como o Rock in Rio, considerando um cenário de alta concorrência e demanda muito superior à quantidade de ingressos disponíveis.

O objetivo é garantir a escalabilidade, a disponibilidade e a consistência das operações, evitando vendas duplicadas e proporcionando uma experiência justa para os usuários.

## 🏗️ Arquitetura proposta

O fluxo principal do sistema é:

**App/Web → WAF → CDN → API Gateway → Fila Virtual → Serviços de Compra**

- **WAF:** protege a aplicação contra ataques e tráfego malicioso.
- **CDN:** distribui conteúdos estáticos, reduzindo a carga sobre os servidores.
- **API Gateway:** centraliza as requisições e encaminha o tráfego para os serviços.
- **Fila virtual:** organiza os usuários por ordem de chegada e controla o acesso à compra.
- **Serviços de compra:** gerenciam reservas, pagamentos e emissão de ingressos.
- **Banco de dados:** garante a consistência do estoque e evita a venda duplicada de ingressos.

## ⚙️ Principais decisões técnicas

- **Escalabilidade horizontal:** permite aumentar a capacidade dos serviços conforme a demanda.
- **Controle de concorrência:** garante que um ingresso não seja vendido para mais de uma pessoa.
- **Reservas temporárias:** os ingressos ficam reservados por um período limitado enquanto o pagamento é realizado.
- **Idempotência:** evita operações duplicadas em caso de retentativas.
- **Resiliência:** trata falhas de pagamento e libera reservas expiradas ou não concluídas.

## 🎯 Objetivo

Demonstrar uma solução arquitetural capaz de lidar com picos extremos de acesso, controlar a concorrência na compra e garantir a integridade do estoque de ingressos.
