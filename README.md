# RavenQuest – Fishing Spots (Silaos) — MVP v1.0

Aplicação web **estática** (HTML/CSS/JS) para marcar e gerenciar *spots* de pesca no mapa do RavenQuest (região Silaos), usando **Leaflet + tiles raster offline** gerados pelo MapTiler Engine.

> Deploy (Netlify):  
> `https://app.netlify.com/projects/revenquestfishingspotsilaos/deploys/69a2e5775a56360008d2c0f0`

---

## O que foi entregue no MVP (v1.0)

### ✅ Mapa offline por tiles (MapTiler Engine)
- Renderização do mapa a partir de tiles locais (`/tiles/{z}/{x}/{y}.png`).
- Leitura automática de configurações via `metadata.json` (zoom, extent, tileSize).
- Detecção do caminho correto dos tiles (boa resiliência entre ambientes local/Netlify).

### ✅ Cadastro e gestão de spots
- Clique no mapa para selecionar a posição.
- Cadastro de spot com:
  - **Nome**
  - **Tags** (separadas por vírgula)
  - **Observação** (opcional)
- Registro automático de **data/hora de criação** do spot (timestamp `createdAt`).

### ✅ Visual e UX focado em usabilidade
- “Preview” do clique com **pino amarelo** (alta visibilidade no mar).
- Spots salvos exibidos como **ponto amarelo pequeno** (discreto e legível sobre fundo azul).
- Interface lateral com orientação de uso e lista dos spots.

### ✅ Persistência local (offline-first)
- Spots salvos no **localStorage** do navegador (funciona offline).
- Chave de storage isolada por tileset (evita misturar spots entre mapas diferentes).

### ✅ Exportação e importação
- Exportar spots para **JSON** (backup/transferência entre dispositivos).
- Importar JSON para restaurar/transferir (com validação básica).

### ✅ Escopo do tipo “spot”
- MVP simplificado para **apenas “Oceano”** (remoção das opções rio/lago).

### ✅ Boas práticas aplicadas no front-end
- Sanitização básica de strings (escape HTML) para evitar XSS em popups/lista.
- Código organizado em blocos (helpers, metadata, mapa, storage, UI).
- Logs de `tileerror` no console para facilitar troubleshooting em deploy.

---

## Estrutura do projeto

```text
/
├─ index.html
├─ metadata.json            (pode estar no root ou dentro de /tiles)
└─ tiles/
   ├─ 0/...
   ├─ 1/...
   ├─ 2/...
   ├─ 3/...
   └─ 4/...

   Limitações conhecidas (MVP)

Não há sincronização em nuvem (apenas localStorage).

Ao trocar o tileset (novo mapa), spots antigos podem não encaixar (depende do extent/escala).

Sem autenticação/usuários; é uma ferramenta single-user.

Próximos passos sugeridos (Roadmap)

Conta/Sync opcional (Firebase/Supabase) mantendo modo offline.

Edição “in-place” (modal) em vez de prompt.

Agrupamento/cluster quando houver muitos spots.

Camadas (ex.: tipos de peixe, horário, isca) e filtros avançados.

Recorte do mapa para remover áreas vazias e reduzir tamanho de tiles.

Créditos e atribuição

Leaflet (map rendering)

Tiles renderizados com MapTiler Engine (uso não comercial conforme export)

A atribuição do MapTiler permanece visível no mapa conforme boas práticas e licenças.

Versão

v1.0 (MVP) — primeira entrega funcional com mapa offline, marcações persistentes, export/import e UI operacional.
