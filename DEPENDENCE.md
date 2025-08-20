# Rembg + Sharp - Modelos U²Net

Este projeto utiliza a biblioteca [`@xixiyahaha/rembg-node`](https://www.npmjs.com/package/@xixiyahaha/rembg-node) junto com [`sharp`](https://www.npmjs.com/package/sharp) para remover fundos de imagens em Node.js.

---

## 📦 Modelos U²Net

O `rembg-node` usa modelos U²Net em formato `.onnx` para fazer segmentação de imagem (remover fundo).
Você precisa baixar manualmente os modelos, pois eles **não vêm incluídos na biblioteca**.

### Modelos disponíveis:

| Modelo                        | Descrição                                             | Tamanho aproximado | Link para download                                                                                    |
| ----------------------------- | ----------------------------------------------------- | ------------------ | ----------------------------------------------------------------------------------------------------- |
| `u2net.onnx`                  | Alta precisão, recortes detalhados de qualquer objeto | 176 MB             | [Download](https://github.com/danielgatis/rembg/releases/download/v0.0.0/u2net.onnx)                  |
| `u2netp.onnx`                 | Versão leve e rápida, menos detalhada                 | 4.7 MB             | [Download](https://github.com/danielgatis/rembg/releases/download/v0.0.0/u2netp.onnx)                 |
| `u2net_human_seg.onnx`        | Especializado em recortar pessoas                     | 4.5 MB             | [Download](https://github.com/danielgatis/rembg/releases/download/v0.0.0/u2net_human_seg.onnx)        |
| `u2net_human_seg_traced.onnx` | Variante otimizada para inferência (pessoas)          | 8 MB               | [Download](https://github.com/danielgatis/rembg/releases/download/v0.0.0/u2net_human_seg_traced.onnx) |

> **Dica:** Para documentos, certificados e objetos gerais, `u2net.onnx` ou `u2netp.onnx` são os mais indicados.

---

## 💻 Onde colocar os arquivos

### Windows

Crie a pasta `.u2net` no seu usuário e coloque os arquivos `.onnx` dentro:

```

C:\Users\<SeuUsuario>\.u2net\

```

Exemplo:

```

C:\Users\joao\.u2net\u2net.onnx
C:\Users\maria\.u2net\u2netp.onnx

```

> O `rembg-node` detecta automaticamente os arquivos nesta pasta.

---

### Linux

Crie a pasta `.u2net` no seu diretório home:

```bash
mkdir -p ~/.u2net
cd ~/.u2net
# Baixe os arquivos
wget https://github.com/danielgatis/rembg/releases/download/v0.0.0/u2net.onnx
wget https://github.com/danielgatis/rembg/releases/download/v0.0.0/u2netp.onnx
```

Depois disso, o Node.js encontrará os modelos automaticamente.

> 💡 Dica: se estiver usando Docker ou outro ambiente de deploy, mantenha a pasta `.u2net` em um **volume persistente** para não precisar baixar de novo.

---

## ⚡ Uso básico em Node.js

```javascript
import { Rembg } from '@xixiyahaha/rembg-node'
import sharp from 'sharp'
;(async () => {
  const input = sharp('./images/teste.jpeg')

  const rembg = new Rembg({ logging: true })

  const output = await rembg.remove(input)

  await output.webp().toFile('test-output.webp')
})()
```

- O modelo padrão usado é `u2net.onnx`.
- Para usar `u2netp.onnx` ou outro modelo, é possível passar a opção `modelPath` no construtor do `Rembg`.

---

## 🔹 Referências

- [@xixiyahaha/rembg-node](https://www.npmjs.com/package/@xixiyahaha/rembg-node)
- [Sharp](https://www.npmjs.com/package/sharp)
- [U²Net GitHub Releases](https://github.com/danielgatis/rembg/releases)
