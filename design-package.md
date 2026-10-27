# Pacote de design: BMW Ferreira, S 1000 RR 2026 (conceito)

Nível 1, uma jornada única. O topo é uma cena animada em código (SVG), sem vídeo gerado: o usuário optou por não usar o Higgsfield. A pasta do site é `bmw-ferreira/`. Este arquivo fica fora dela.

## 1. A premissa da marca

**Apresentação particular.** Uma superesportiva de 210 cv não é vendida em vitrine. Ela é apresentada num showroom escuro, com as luzes acesas uma por vez, só para você. Cada seção do site serve a essa ideia: a cena de abertura acende o showroom, a seção "Sem surpresas" esclarece as dúvidas, a interação dá a partida no motor e o único botão de ação agenda uma visita privada.

## 2. Paleta (tokens CSS)

```css
:root{
  --canvas:#0F1217;        /* grafite azulado, a parede do showroom */
  --panel:#161B22;
  --accent:#8FB0CC;        /* azul Bluestone, só no botão de ação, no foco e na faixa vermelha do conta-giros */
  --accent-hover:#A9C4DB;
  --accent-muted:rgba(143,176,204,.16);
  --text-secondary:#9AA1AA;
  --text-primary:#ECE9E3;  /* platina */
}
```

## 3. Trio de fontes

- Títulos: **Archivo Expanded** (largura 125), pesos 300 e 600. Larga e elegante, como uma carenagem.
- Texto corrido: **Instrument Sans**, pesos 400 e 500.
- Rótulos: **JetBrains Mono**, peso 400.

## 4. Mapa das faixas (topo, 600vh)

| Faixa | Intervalo (ponto de partida) | Cena | Texto (exato) | Entrada |
|---|---|---|---|---|
| 1 | 0,00 a 0,17 | Showroom escuro, moto só em contorno | "BMW Ferreira · Jardins" / "A nova S 1000 RR 2026." / "Uma apresentação particular. Role para acender as luzes." | Palavras sobem (rampa ao carregar) |
| 2 | 0,20 a 0,38 | O primeiro holofote acende a frente | "01 · Frente" / "210 cv. Ainda em silêncio." / "Quatro cilindros, 999 cm³, 13.750 rpm." | Desfocado para nítido (os olhos se ajustando à luz) |
| 3 | 0,42 a 0,60 | O segundo holofote acende as asas e o tanque | "02 · Aerodinâmica" / "Asas que seguram a moto no chão." / "Até 37% mais pressão aerodinâmica que a geração anterior." | Letras deslizam na horizontal (o ar passando) |
| 4 | 0,64 a 0,80 | O terceiro holofote acende a traseira e o escapamento | "03 · Traseira" / "Akrapovič de série." / "E feita no Brasil, em Manaus. A BMW mais potente montada aqui." | Letras se juntam como calor que se dispersa |
| 5 | 0,84 a 1,00 | Showroom inteiro aceso, farol ligado | "Agora ela é toda sua. Por uma tarde." / "Visitas privadas no showroom dos Jardins, com hora marcada." / [Agendar visita privada] [Ver as versões] | Palavras sobem, depois texto, depois botões |

## 5. Topo estático (movimento reduzido)

O showroom aceso por completo, com a faixa 5 visível: "Agora ela é toda sua. Por uma tarde." + texto + botões.

## 6. Seções abaixo do topo

1. **A máquina:** 210 cv · 999 cm³ · 13.750 rpm · 7 modos. "Rain, Road, Dynamic, Race e três modos Race Pro. Kit Chassi M e escapamento Akrapovič em todas as versões."
2. **Quatro versões:** Preta R$ 139.900 · Cinza Bluestone R$ 141.900 · M Package R$ 158.900 · M Carbon R$ 178.900. Observação: preços sugeridos de lançamento, confirmados na visita; cores ilustrativas. A moto da cena final é reutilizada, mudando de cor conforme a versão.
3. **Sem surpresas:** quatro dúvidas reais dos compradores, respondidas diretamente (manutenção, seguro, uso diário, revenda).
4. **Como é a visita:** três passos com uma ilustração cada.
5. **Momento interativo (Partida):** segure o botão para levar o conta-giros até o vermelho. Soltar antes faz o ponteiro voltar devagar. Ao completar, a lista "Sua visita inclui" acende item por item.
6. **Perguntas:** iniciante, custo anual, financiamento, pista, preços.
7. **Agendar (a única ação):** nome, WhatsApp, versão, período. Só mostra a mensagem de sucesso no navegador: é um projeto de demonstração, então nada é enviado, e o site diz isso claramente.
8. **Rodapé:** aviso de que é um conceito, de que a BMW Ferreira não existe e de que o site não é um anúncio oficial da BMW. BMW e S 1000 RR são marcas da BMW AG.

Sem depoimentos: num conceito, eles seriam inventados. A prova vem dos fatos públicos da moto.

## 7. Camada vetorial

Moto em perfil desenhada à mão em SVG, com feixes e poças de luz dos holofotes, reflexo no chão e poeira flutuando nos feixes. Uma linha de traçado de pista que se desenha conforme a rolagem em "A máquina" e na linha do tempo da visita. Um fundo fixo com granulado e um brilho suave que se move num ciclo de 90 segundos. Com movimento reduzido, tudo aparece no estado final.

## 8. Lista de engenharia

Interpolação suave da rolagem ajustada ao tempo de cada quadro (lerp com dt), com laço rAF que para quando a cena estabiliza ou sai da tela; escritas no DOM só quando algo muda; faixas com platôs longos e o teste de rolagem rápida; quatro camadas de legibilidade; movimento reduzido ao vivo nos dois sentidos; padrão mínimo de qualidade. Sem vídeo, então não há carregamento de Blob, controle de buscas no vídeo nem os cinco bloqueios de topo estático. Mudança assumida: o celular recebe a cena animada, porque ela pesa poucos KB.

## 9. Revisão do texto

Todo texto acima vai para o site exatamente como está. A página precisa passar na revisão da Fase 9: zero travessões, zero palavras genéricas de marketing e a varredura de vícios de texto de IA.
