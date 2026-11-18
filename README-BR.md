# Stream Cipher: OTP e Two-Time Pad

Este repositório demonstra, em Python, o funcionamento de cifras de fluxo e o risco da reutilização de uma mesma chave ou keystream.

O projeto apresenta exemplos práticos de:

- Criptografia com XOR
- One-Time Pad
- Ataque conhecido como **Two-Time Pad**
- Combinação de dois textos cifrados
- Recuperação parcial de mensagens por *crib dragging*

## Estrutura do repositório

- `stream-cipher.py`: demonstra criptografia e descriptografia de bits com XOR e reutilização da chave.
- `exemplo1.py`: apresenta o ataque Two-Time Pad com mensagens em bytes.
- `exemplo2.py`: demonstra uma análise estatística baseada em espaços.
- `lousa-aula-blockchain.png`: material visual utilizado como apoio didático.
- `LICENSE`: licença MIT do projeto.

## Como funciona

Uma cifra de fluxo gera um keystream `K` e combina esse valor com a mensagem `M` por meio da operação XOR:

```text
C = M XOR K
M = C XOR K
```

Como o XOR aplicado duas vezes com o mesmo valor recupera o dado original, o mesmo keystream pode ser usado para cifrar e decifrar.

## Cenários demonstrados

### One-Time Pad

O arquivo `stream-cipher.py` aplica XOR a uma mensagem binária e a um keystream:

```text
M = 10110011
K = 11001010
C = M XOR K
```

A mesma operação é utilizada para decifrar o texto cifrado.

### Ataque Two-Time Pad

Quando duas mensagens são cifradas com o mesmo keystream:

```text
C1 = M1 XOR K
C2 = M2 XOR K
```

Um atacante pode calcular:

```text
C1 XOR C2 = M1 XOR M2
```

Assim, a chave é eliminada da equação e a relação entre os dois textos originais é revelada.

Os exemplos `exemplo1.py` e `exemplo2.py` demonstram como essa vulnerabilidade pode ser explorada:

- Reutilização da mesma chave em mais de uma mensagem
- Comparação entre textos cifrados
- Chutes de palavras conhecidas, ou *crib dragging*
- Identificação de espaços e caracteres por análise estatística

## Executando o projeto

Não são necessárias dependências externas.

```bash
git clone https://github.com/rique-decoder/stream-cipher-otp-twotimepad-implementation.git
cd stream-cipher-otp-twotimepad-implementation
```

Execute os exemplos:

```bash
python stream-cipher.py
python exemplo1.py
python exemplo2.py
```

## Considerações de segurança

A reutilização de uma chave em uma cifra de fluxo é insegura. Para que uma cifra XOR baseada em pad seja efetivamente segura, o keystream deve:

- Ser aleatório
- Ter tamanho suficiente
- Ser usado apenas uma vez
- Ser mantido em segredo

Este repositório possui finalidade educacional e não deve ser utilizado como implementação criptográfica para sistemas reais.

## Licença

Este projeto está disponível sob a licença MIT.