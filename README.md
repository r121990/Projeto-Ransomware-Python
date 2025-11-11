# FERNET FILE ENCRYPTOR (EXEMPLO EDUCACIONAL)

> **AVISO IMPORTANTE:** este repositório contém exemplos educativos de criptografia simétrica usando a biblioteca `cryptography` (Fernet). **NÃO** use estes scripts em computadores com arquivos importantes, em sistemas de produção ou para atividades que causem dano a terceiros. Execute-os **somente** em um ambiente de teste controlado (por exemplo, uma pasta `test_files` criada para experimentos) e em máquinas que você possua/permissão para testar.

---

## Objetivo

Projeto demonstrativo para aprender como funciona a criptografia simétrica com `Fernet` (biblioteca `cryptography`), mostrando:

* como gerar e salvar uma chave segura;
* como criptografar e descriptografar arquivos de forma simples;
* noções básicas de segurança e de boas práticas ao lidar com chaves.

Este projeto é **educacional** — não é uma ferramenta de backup robusta nem um produto pronto para produção.

---

## Estrutura do repositório

```
.
├── ransomware.py       # script para gerar chave e criptografar arquivos (educacional)
├── descriptografar.py  # script para descriptografar arquivos usando a chave gerada
├── chave.key           # (gerada durante o uso) chave Fernet — NÃO comite no git
├── test_files/         # pasta de exemplo para testar (crie seus arquivos aqui)
├── images/             # pasta com capturas de tela das execuções
└── README.md
```

> **Nunca** commite `chave.key` ao controle de versão. Adicione `chave.key` ao `.gitignore`.

---

## Requisitos

* Python 3.8+
* Biblioteca `cryptography`

Instalar com:

```bash
pip install cryptography
```

---

## Uso seguro (passo a passo)

1. Crie uma pasta chamada `test_files` no diretório do projeto e coloque nela **somente** arquivos de teste (arquivos que você pode apagar/alterar sem prejuízo).
2. Garanta que você tem backup dos seus arquivos reais — **não execute** este projeto em arquivos importantes.
3. Execute o script de criptografia (exemplo):

```bash
python ransomware.py
```

* O script deve gerar `chave.key` e criptografar os arquivos dentro de `test_files`.
* Verifique o conteúdo de `test_files` — os arquivos estarão encriptados (binários ilegíveis).

4. Para restaurar os arquivos de teste, execute o script de descriptografia:

```bash
python descriptografar.py
```

* Ele utilizará `chave.key` para restaurar os dados originais.

---

## Boas práticas e considerações de segurança

* **Nunca** execute scripts que criptografam arquivos fora de um diretório de teste controlado.
* **Não** armazene a chave (`chave.key`) em repositórios públicos. Trate a chave como um segredo — armazene-a em local seguro (cofre de segredos) se for necessário manter para uso legítimo.
* Faça backups antes de qualquer operação que modifique arquivos.
* Para qualquer uso real de criptografia em produção, consulte um especialista em segurança e siga padrões de gerenciamento de chaves (KMS, rotacionamento, políticas de acesso).

---

## Como funciona (resumo técnico)

* `Fernet` implementa criptografia simétrica autenticada, garantindo confidencialidade e integridade.
* Fluxo básico:

  1. Gera-se uma chave segura (`Fernet.generate_key()`).
  2. Ao criptografar um arquivo, o conteúdo é lido em binário, passado para `Fernet.encrypt()` e escrito de volta.
  3. Descriptografia usa a mesma chave e `Fernet.decrypt()`.

---

## Exemplo de saída / comportamento esperado

* Antes: `test_files/exemplo.txt` com texto legível.
* Depois de `ransomware.py`: `test_files/exemplo.txt` com conteúdo binário (não legível).
* Depois de `descriptografar.py`: `test_files/exemplo.txt` restaurado ao texto original.

## Contato / Notas finais

Rafael Kmohan  Paulino Patricio
rkmohanpp@gmail.com

Reforçando: não ajudo a produzir, documentar ou distribuir software com finalidade de causar dano ou extorquir terceiros. Todos projetos são para fins educacionais de cybersegurança.