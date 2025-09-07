# Linux Permissions Evidence (GitHub Actions)

Este projeto cria um ambiente de teste em **Linux** usando **GitHub Actions** para automatizar a atividade de permissões, donos e acessos a arquivos.  
Ele gera uma **imagem PNG com os logs** (em vez de prints de tela manuais), que pode ser usada como evidência para entrega da atividade.

## O que o workflow faz
1. Cria os diretórios:
   - `Scripts/`
   - `Logs/`
   - `App/`

2. Cria os arquivos:
   - `Scripts/3ESPW.sh`
   - `Logs/relatorio.log`
   - `App/disposition.app`

3. Define permissões:
   - `3ESPW.sh`: `-rwxr-xr-x` (755)
   - `relatorio.log`: `-rwxrwx---` (770)
   - `disposition.app`: `-r-xr-xr-x` (555)

4. Troca o dono dos arquivos:
   - `3ESPW.sh` → `root`
   - `disposition.app` → `root`

5. Garante que todos possam acessar e listar os diretórios criados.

6. Executa:
   - `ls -lR /home/runner` para listar tudo recursivamente.
   - Acesso de outro usuário (`rm98344`) simulando a leitura dos arquivos.

7. Gera um **arquivo de imagem (`evidence.png`)** com os logs coletados.

## Como rodar
1. Vá até a aba **Actions** do repositório no GitHub.  
2. Execute o workflow **Linux Permissions Evidence** manualmente (`workflow_dispatch`).  
3. Aguarde a execução.  
4. Baixe os artefatos gerados (em `evidence.png`).  

## Entregável
O arquivo **evidence.png** contém os logs pedidos na atividade e pode ser anexado como resposta da tarefa.
