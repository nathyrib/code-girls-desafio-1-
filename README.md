Desafio 1 - Gerenciando Instâncias EC2 na AWS 

Aprendizados do curso

Amazon EC2

• EC2 (Elastic Computing Cloud) é um serviço de máquinas virtuais dentro da AWS;
• Possibilita que qualquer aplicação rode na nuvem de forma simples e elástica;
• Ele é distribuído nas máquinas virtuais em vários datacenters em todo mundo, o que permite que mesmo se houver algum problema em alguma das máquinas o serviço continue funcionando;
• O usuário paga apenas pelo uso.

Amazon RDS

•RDS (Relational Database Service) permite a criação e a utilização de bancos de dados na nuvem.

Amazon EBS

• EBS (Elastic Block Store) oferece armazenamento para instâncias EC2;
• Permite backups automáticos chamados snapshots.

Amazon S3

• S3(Simple Storage Service) é um serviço de armazenamento em nuvem que permite guardar arquivos de forma segura e escalável;
• Os arquivos são armazenados em buckets. Cada bucket pode conter milhares de arquivos, e o usuário pode acessar esses dados pela internet, de qualquer lugar do mundo. 


Diferença entre EC2 e S3

O EC2 é utilizado para criar servidores virtuais na nuvem. Ele pode rodar sites, sistemas, aplicativos ou qualquer coisa que precise de processamento.
Já o S3 é usado para guardar arquiv) é um serviço de armazenamento em nuvem que permite guardar arquivos de forma segura, acessível e escalável. os na nuvem. Ele pode armazenar fotos, vídeos, documentos e etc.


Explicação do diagrama

Nesse desafio foi pedido uma arquitetura com EC2 |EBS |S3 |Lambda Function. Decidi por usar um cenário para exemplificar essa arquitetura. O cenário  escolhido foi um sistema escolar, 
onde um professor pode entrar para ter acesso aos dados da escola e lançar as notas dos alunos. Com isso, temos as seguintes relações:

O usuário (professor) acessa o sistema escolar através da Internet, que encaminha a requisição para os recursos hospedados na nuvem. A requisição passa pelo Internet Gateway, que é o ponto de entrada da rede externa para a VPC da escola. Ele permite que os usuários externos se comuniquem com os recursos internos da AWS. 
Dentro da VPC, o Security Group controla o acesso conforme as regras de segurança. A requisição então chega à EC2, onde está hospedado o sistema escolar. Essa aplicação trata os dados, confirma a identidade do usuário e mostra as informações solicitadas.
Os dados dos alunos são armazenados em um EBS conectado à EC2. Registros organizados como alunos, desciplinas e notas, podem ser armazenadas em um banco de dados RDS.
A EC2 acessa o S3 com permissões definidas pelo IAM Role, e essa instância envia arquivos para o S3. Materiais como PDFs, imagens e vídeos ficam no S3, que garante espaço e segurança.
