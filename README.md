Desafio 1 - Gerenciando Instâncias EC2 na AWS 

Aprendizados do curso

Explicação do diagrama

Nesse desafio foi pedido uma arquitetura com EC2 |EBS |S3 |Lambda Function. Decidi por usar um cenário para exemplificar essa arquitetura. O cenário  escolhido foi um sistema escolar, 
onde um professor pode entrar para ter acesso aos dados da escola e lançar as notas dos alunos. Com isso, temos as seguintes relações:

O usuário (professor) acessa o sistema escolar através da internet, que encaminha a requisição para os recursos hospedados na nuvem. A requisição passa pelo Internet Gateway, que é o ponto de entrada da rede externa para a VPC da escola. Ele permite que os usuários externos se comuniquem com os recursos internos da AWS. 
Dentro da VPC, o tráfego é filtrado pelo Security Group, que permite ou bloqueia acessos com base em regras de segurança. A requisição então chega à Instância EC2, onde está hospedado o sistema escolar. Essa aplicação processa os dados, autentica o usuário e exibe as informações solicitadas.
Os dados do aluno são armazenados em um EBS conectado à EC2.
Rrgistros organizados como alunos, desciplinas e notas, podem ser armazenadas em um banco de dados RDS.
A EC2 acessa o S3 usando permissões definidas por IAM Role, 
Arquivos de apoio como PDFs, imagens e vídeos, podem ser armazenados no S3, que oferece armazenamento escalável e seguro.
