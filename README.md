# 📍 Buscador de Clínicas Personalizado (Store Locator)

Este projeto consiste na implementação e personalização avançada de um sistema de localização de clínicas (Store Locator) utilizando WordPress. 
O objetivo foi transformar um plugin padrão em uma ferramenta de busca intuitiva, visualmente alinhada à marca e capaz de exibir dados complexos (equipamentos disponíveis) diretamente nos resultados.

## 🚀 Funcionalidades Principais

* **Busca por Geolocalização:** Integração com Google Maps API para busca por CEP ou endereço atual.
* **Design Customizado:** Interface limpa desenvolvida com CSS Grid e Flexbox, substituindo o layout padrão do plugin.
* **Dados Personalizados:** Exibição dinâmica de "Equipamentos/Tecnologias" em etiquetas (tags) dentro de cada card.
* **Rotas Inteligentes:** Geração automática de links para navegação (Google Maps/Waze).
* **Responsividade:** Layout adaptado para Mobile e Desktop.

## 🛠️ Tecnologias Utilizadas

* **CMS:** WordPress
* **Plugin Base:** WP Store Locator
* **Frontend:** CSS3 (Custom), Elementor (Layout Base)
* **Backend:** PHP (Snippets para manipulação de template e hooks)
* **Dados:** Excel/CSV (Tratamento de dados)
* **API:** Google Maps (Geocoding & Maps JavaScript)

## ⚙️ Etapas do Desenvolvimento

### 1. Tratamento e Limpeza de Dados (Data Cleaning)
O sucesso do buscador dependia da precisão dos dados. O processo envolveu:
* Padronização de endereços no Excel para garantir geocodificação precisa (Lat/Long).
* Limpeza de caracteres especiais e formatação de CEPs.
* Estruturação da coluna de **Categorias** para conter os equipamentos (ex: "Laser Crystal 3D, Hipro").
* Exportação de um CSV otimizado para importação em massa, garantindo integridade dos dados.

### 2. Implementação Técnica (PHP Snippets)
O plugin nativo não exibia as categorias/equipamentos da forma desejada. Foi necessário injetar código via `functions.php` (ou Code Snippets) para alterar o template de renderização.

**Solução para Exibir Equipamentos:**
Utilizei o filtro `wpsl_listing_template` para reescrever o HTML do card, capturando os termos da taxonomia `wpsl_store_category` e renderizando-os como etiquetas visuais.

```php
 Exemplo da lógica utilizada para capturar os dados
add_filter( 'wpsl_store_meta', function( $store_meta, $store_id ) {
    $terms = get_the_terms( $store_id, 'wpsl_store_category' );
     ... lógica de tratamento ...
    return $store_meta;
}, 10, 2 );
3. Customização Visual (CSS)
Para fugir do visual genérico, apliquei CSS personalizado focando em UX:

Cards: Uso de sombras suaves e bordas arredondadas.

Etiquetas: Styling das categorias com cores de destaque (Fundo Azul Claro/Texto Escuro).

Layout: Centralização do buscador e alinhamento do mapa com a lista de resultados (max-width: 1140px).

📸 Screenshots
(Espaço reservado para você colocar prints do antes e depois)

📄 Como utilizar
Importe o arquivo .csv tratado através do painel do plugin.

Configure as chaves de API do Google Maps.

Adicione os Snippets PHP listados na pasta /src.

Insira o shortcode [wpsl] na página desejada.

Desenvolvido por Ramon Silva
