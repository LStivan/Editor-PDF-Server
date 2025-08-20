# Editor-PDF-Server – Remoção de Fundo Inteligente para Imagens

O **Editor-PDF-Server** é um módulo Node.js especializado em **remoção automática de fundos de imagens** utilizando inteligência artificial. Ele combina o poder do [`@xixiyahaha/rembg-node`](https://www.npmjs.com/package/@xixiyahaha/rembg-node) com a performance do [`sharp`](https://www.npmjs.com/package/sharp), oferecendo uma solução rápida e precisa para edição de imagens, especialmente útil para documentos, certificados, fotos de pessoas e objetos gerais.

### Principais características:

- **Remoção automática de fundo** com modelos U²Net de alta precisão.
- **Suporte a múltiplos modelos**: desde versões leves (`u2netp.onnx`) até modelos especializados em recorte de pessoas (`u2net_human_seg.onnx`).
- **Integração com Sharp** para manipulação avançada de imagens (resize, conversão de formatos, compressão, etc.).
- **Configuração simples**: basta colocar os modelos `.onnx` em uma pasta padrão (`.u2net`) e o módulo detecta automaticamente.
- **Flexível e escalável**: funciona em Windows, Linux e ambientes Docker com volumes persistentes.

### Casos de uso:

- Preparação de imagens para PDFs, apresentações ou sites.
- Remoção de fundo em fotos de produtos, e-commerce ou marketing.
- Extração de objetos ou pessoas de fotos para colagens, composições ou efeitos gráficos.

### Tecnologias utilizadas:

- **Node.js**
- **@xixiyahaha/rembg-node** (IA de segmentação de imagens)
- **Sharp** (manipulação de imagens)
- **Modelos U²Net (.onnx)** para diferentes tipos de recorte

> Um projeto simples, rápido e altamente eficiente para quem precisa automatizar a remoção de fundo de imagens sem perder qualidade.
