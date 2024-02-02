## Configurar o NFS
<p>Com o devido acesso ao Console AWS, será necessário seguir as seguintes etapas:</p>
<ol>
  <li>Acessar, pelo console, o serviço EFS</li>
  <li>Clicar no botão <i>Criar Sistema de arquivos</i></li>
</ol>
A partir desses passos será aberta a janela para preenchimento de dados.
<ul>
  <li>Clicar no botão <i>Personalizar</i></li>
  <ul>
    <li>Nome: <ins>EFS-Projeto</ins></li>
    <li>Todas as opções foram mantidas e cliquei em <i>Próximo</i></li>
    <li>Redes: confirmei que estava usando meu grupo de segurança padrão</li>    
    <li><b>Importante:</b> fui até meu grupo de segurança e fiz a liberação da porta 2049 TCP/UDP</li>
    <li>Clicar em <i>Próximo</i></li>
  </ul>
  <li>Não fiz alterações nas políticas. Clique em <i>Próximo</i> e na próxima tela clique no botão <i>Criar</i></li>
</ul>
Após aguardar a criação do Sistema de arquivos, proceder da seguinte maneira:
<ul>
  <li>Selecionar o Sistema de Arquivos criado: <i>EFS-Projeto</i></li>
  <li>Clique no botão <i>Visualizar Detalhes</i></li>
  <li>Clique no botão <i>Anexar</i></li>
  <li>Com a opção <i>Montar via DNS</i> selecionada, copie a linha de comando referente a opção <i>Usando o assistente de montagem do EFS</i> </li>
</ul>
Usando uma máquina virtual Linux previamente criada, fiz o acesso à minha Instância criada anteriormente.
Ao concluir o acesso, os seguintes passos devem ser feitos:
<ul>
  <li>Instalar o programa <i>amazon-efs-utils</i></li>
  <code>sudo yum install amazon-efs-utils -y</code>
  <li>Crie um novo diretório</li>
  <code>mkdir <i>nome-da-pasta</i></code>
  <li>Após a criação do diretório, cole o comando copiado do console AWS</li>
  <code>sudo mount -t efs -o tls fs-xxxxxxxxxxxxx:/ <i>nome-da-pasta</i></code>
</ul>

## Criar um diretório dentro do filesystem do NFS com meu nome
<ul>
  <li>Dentro da instância, dentro do diretório criado para o EFS, crie um novo diretório</li>
  <code>sudo mkdir <i>meu-nome</i></code>
  <li>Depois da montagem, para garantir o funcionamento, crie uma instância e repita o processo de configuração do NFS</li>
  <li>Se tudo estiver correto, será possível visualizar o diretório <i>meu-nome</i> em ambas instâncias</li>
</ul>

## Subir um apache no servidor
