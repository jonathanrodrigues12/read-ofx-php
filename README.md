# 📄 Leitor de Arquivos OFX em PHP

**Autor:** Jonathan Rodrigues

## 📘 Visão Geral

Este repositório contém um **script simples em PHP** que permite ler arquivos OFX (Open Financial Exchange) e extrair suas informações em um formato utilizável. Ele pode ser útil para sistemas de controle financeiro, importação de extratos bancários ou integração com bancos que fornecem arquivos OFX.

## 🚀 Funcionalidades

- Leitura de arquivos OFX.
- Extração de informações bancárias como:
  - Código do banco
  - Número da conta
  - Nome da instituição financeira
- Listagem de transações financeiras do extrato.
- Identificação de data de início e fim do extrato.

## 🛠️ Requisitos

- PHP 5.6 ou superior
- Extensão `mbstring` habilitada

## 📦 Como usar

1. **Clone este repositório:**

```bash
git clone https://github.com/jonathanrodrigues12/read-ofx-php.git
```

2. **Inclua o script no seu projeto PHP:**

```php
require_once 'leituraofx/Ofx.php';
```

3. **Exemplo de execução:**

```php
<?php
require_once 'leituraofx/Ofx.php';

// Caminho para o arquivo OFX
$ofx = new Ofx("caminho/para/seu.arquivo.ofx");

// Informações gerais
echo "Data de Início: " . $ofx->dtStar . PHP_EOL;
echo "Data de Fim: " . $ofx->dtEnd . PHP_EOL;
echo "Código do Banco: " . $ofx->bankId . PHP_EOL;
echo "Número da Conta: " . $ofx->acctId . PHP_EOL;
echo "Nome da Instituição: " . $ofx->org . PHP_EOL;

// Transações
foreach ($ofx->bankTranList as $t) {
    echo "Data: {$t['DTPOSTED']}" . PHP_EOL;
    echo "Tipo: {$t['TRNTYPE']}" . PHP_EOL;
    echo "Valor: {$t['TRNAMT']}" . PHP_EOL;
    echo "Descrição: {$t['MEMO']}" . PHP_EOL;
    echo "------------------------" . PHP_EOL;
}
?>
```

## 📝 Observações

- O script realiza parsing básico do OFX em texto plano. É possível estendê-lo para lidar com variações de layout e mais campos conforme necessidade.
- Garanta que o arquivo esteja em UTF-8 para evitar erros de codificação.

## 📄 Licença

Este projeto está licenciado sob a [Licença MIT](LICENSE).
