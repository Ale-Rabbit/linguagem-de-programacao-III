# Aula de Linguagem de Programação III
Repositório GIT para ajudar os colegas do IFSUL nas atividades da matéria de Linguagem de Programação III.

Para acessar as classes basta ir nas pastas acima (Aula 1/4iLP3 > src)

Atalhos:

- [Configuração do Ambiente](#configuração-do-ambiente)

# Configuração do Ambiente
Passo a passo da configuração do ambiente:

- Fazer o download da última versão do [Hibernate](http://hibernate.org/orm/) e do [MySQL Connector](https://dev.mysql.com/downloads/connector/j/);
- Descompactar o arquivo do Hibernate (no linux: abrir o terminal e executar o comando `unzip NOME_DO_ARQUIVO`);
- Abrir o eclipse e ir em `File` ->  `New` -> `JPA Project`.

Ao abrir a modal `New JPA Project`:

- Informar o `Project Name`;
- Alterar o `Target runtime` para `java-8-oracle`;
- Clicar em `Next`;
- Clicar em `Next`;
- Clicar em `Manage Libraries`.

Ao Abrir a modal `Preferences(Filtered)`:
- Clicar em `New`;
- Informar o `User library name` (sugestão: hibernate);
- Selecionar a `library` criada e clicar em `Add External JARs...` ;
- Navegar até a pasta que contêm o hibernate descompactado (algo como: `~\hibernate-release-x.x.x.Final`);
- Selecionar todos os arquivos `.jar`dentro do caminho `\lib\required`;
- Clicar em `enter`.

Repetir o processo novamente para o MySQL Connector:
- Clicar em `New`;
- Informar o `User library name` (sugestão: mysql);
- Selecionar a `library` criada e clicar em `Add External JARs...` ;
- Navegar até a pasta que contêm o MySQL Connector;
- Selecionar o arquivo do MySQL Connector (`mysql-connector-java-x.x.xx-bin.jar`);
- Clicar em `enter`.

Feito isto:
- Clicar em OK na modal `Preferences(Filtered)`;
- Selecionar as duas bibliotecas criadas em JPA Implementation;
- Selecionar a opção `Discover annotated classes automatically` em `Persistent class management`
    para as classes criadas serem adicionadas automaticamente no `persistence.xml`;
- Clicar em `finish` e está pronto o sorvetinho.

## Persistence.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<persistence version="2.1" xmlns="http://xmlns.jcp.org/xml/ns/persistence" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/persistence http://xmlns.jcp.org/xml/ns/persistence/persistence_2_1.xsd">
    <persistence-unit name="Aula1_4I" transaction-type="RESOURCE_LOCAL">
        <provider>org.hibernate.jpa.HibernatePersistenceProvider</provider>   
        <class>Pessoa</class>
        <properties>
            <property name="javax.persistence.jdbc.driver" value="com.mysql.jdbc.Driver"/>
            <property name="javax.persistence.jdbc.user" value="root"/>
            <property name="javax.persistence.jdbc.password" value="ifsul2017"/>
            <property name="javax.persistence.jdbc.url" value="jdbc:mysql://localhost:3306/4i"/>
            <property name="hibernate.dialect" value="org.hibernate.dialect.MySQL5InnoDBDialect"/>
            <property name="hibernate.show_sql" value="true"/>
            <property name="hibernate.format_sql" value="true"/>
            <property name="hibernate.use_sql_comments" value="false"/>
            <property name="hibernate.hbm2ddl.auto" value="update"/>       
        </properties>
        </persistence-unit>
</persistence>
``` 
## Banco de Dados

Criar o banco de dados antes de rodar a classe `Executavel`.
O nome do BD deve ser igual ao informado na tag 
```xml 
<property name="javax.persistence.jdbc.url" value="jdbc:mysql://localhost:3306/4i"/>
```
onde o nome do BD deve ser passado como ultimo parametro, depois da porta em value="jdbc:mysql://localhost:3306/**4i**".
```sql
CREATE DATABASE 4i;
```
