# Api-java

<?xml version="1.0" encoding="UTF-8"?>
<classpath>
	<classpathentry kind="src" output="target/classes" path="src/main/java">
		<attributes>
			<attribute name="optional" value="true"/>
			<attribute name="maven.pomderived" value="true"/>
		</attributes>
	</classpathentry>
	<classpathentry excluding="**" kind="src" output="target/classes" path="src/main/resources">
		<attributes>
			<attribute name="maven.pomderived" value="true"/>
		</attributes>
	</classpathentry>
	<classpathentry kind="src" output="target/test-classes" path="src/test/java">
		<attributes>
			<attribute name="optional" value="true"/>
			<attribute name="maven.pomderived" value="true"/>
		</attributes>
	</classpathentry>
	<classpathentry excluding="**" kind="src" output="target/test-classes" path="src/test/resources">
		<attributes>
			<attribute name="maven.pomderived" value="true"/>
		</attributes>
	</classpathentry>
	<classpathentry kind="con" path="org.eclipse.jdt.launching.JRE_CONTAINER/org.eclipse.jdt.internal.debug.ui.launcher.StandardVMType/JavaSE-1.8">
		<attributes>
			<attribute name="maven.pomderived" value="true"/>
		</attributes>
	</classpathentry>
	<classpathentry kind="con" path="org.eclipse.m2e.MAVEN2_CLASSPATH_CONTAINER">
		<attributes>
			<attribute name="maven.pomderived" value="true"/>
		</attributes>
	</classpathentry>
	<classpathentry kind="output" path="target/classes"/>
</classpath>
 29  .project 
@@ -0,0 +1,29 @@
<?xml version="1.0" encoding="UTF-8"?>
<projectDescription>
	<name>clientes</name>
	<comment></comment>
	<projects>
	</projects>
	<buildSpec>
		<buildCommand>
			<name>org.eclipse.jdt.core.javabuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>org.hibernate.eclipse.console.hibernateBuilder</name>
			<arguments>
			</arguments>
		</buildCommand>
		<buildCommand>
			<name>org.eclipse.m2e.core.maven2Builder</name>
			<arguments>
			</arguments>
		</buildCommand>
	</buildSpec>
	<natures>
		<nature>org.eclipse.jdt.core.javanature</nature>
		<nature>org.eclipse.m2e.core.maven2Nature</nature>
		<nature>org.hibernate.eclipse.console.hibernateNature</nature>
	</natures>
</projectDescription>
 6  .settings/org.eclipse.core.resources.prefs 
@@ -0,0 +1,6 @@
eclipse.preferences.version=1
encoding//src/main/java=UTF-8
encoding//src/main/resources=UTF-8
encoding//src/test/java=UTF-8
encoding//src/test/resources=UTF-8
encoding/<project>=UTF-8
 5  .settings/org.eclipse.jdt.core.prefs 
@@ -0,0 +1,5 @@
eclipse.preferences.version=1
org.eclipse.jdt.core.compiler.codegen.targetPlatform=1.8
org.eclipse.jdt.core.compiler.compliance=1.8
org.eclipse.jdt.core.compiler.problem.forbiddenReference=warning
org.eclipse.jdt.core.compiler.source=1.8
 4  .settings/org.eclipse.m2e.core.prefs 
@@ -0,0 +1,4 @@
activeProfiles=
eclipse.preferences.version=1
resolveWorkspaceProjects=true
version=1
 3  .settings/org.hibernate.eclipse.console.prefs 
@@ -0,0 +1,3 @@
default.configuration=clientes
eclipse.preferences.version=1
hibernate3.enabled=true
 1  gitignore 
@@ -0,0 +1 @@
target 
 56  pom.xml 
@@ -0,0 +1,56 @@
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>1.3.3.RELEASE</version>
	</parent>

	<groupId>br.fa7.spring.loja</groupId>
	<artifactId>clientes</artifactId>
	<version>0.0.1-SNAPSHOT</version>

	<properties>
		<java.version>1.8</java.version>
	</properties>

	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-jersey</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-aop</artifactId>
		</dependency>
		<dependency>
			<groupId>org.hsqldb</groupId>
			<artifactId>hsqldb</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-devtools</artifactId>
			<optional>true</optional>
		</dependency>

	</dependencies>
	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

</project> 
 14  src/main/java/br/edu/fa7/clientes/JerseyConfig.java 
@@ -0,0 +1,14 @@
package br.edu.fa7.clientes;

import org.glassfish.jersey.server.ResourceConfig;
import org.springframework.context.annotation.Configuration;

import br.edu.fa7.clientes.resources.ClienteResource;

@Configuration
public class JerseyConfig extends ResourceConfig {

	public JerseyConfig() {
		register(ClienteResource.class);
	}
}
 14  src/main/java/br/edu/fa7/clientes/Main.java 
@@ -0,0 +1,14 @@
package br.edu.fa7.clientes;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class Main {

	public static void main(String[] args) {
		System.setProperty("server.port", "8082");
		SpringApplication.run(Main.class, args);
	}
}

 72  src/main/java/br/edu/fa7/clientes/model/Cliente.java 
@@ -0,0 +1,72 @@
package br.edu.fa7.clientes.model;

import java.io.Serializable;
import java.util.List;

import javax.persistence.CascadeType;
import javax.persistence.Entity;
import javax.persistence.FetchType;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;
import javax.persistence.OneToMany;

@Entity
public class Cliente implements Serializable{

	private static final long serialVersionUID = 1351114571090543262L;

	@Id
	@GeneratedValue(strategy=GenerationType.IDENTITY)
	private Long id;

	private String nome;

	private String email;

	private String login;

	@OneToMany(fetch=FetchType.EAGER, cascade=CascadeType.ALL, orphanRemoval= true, mappedBy="cliente")
	private List<Endereco> enderecos;

	public Long getId() {
		return id;
	}

	public void setId(Long id) {
		this.id = id;
	}

	public String getNome() {
		return nome;
	}

	public void setNome(String nome) {
		this.nome = nome;
	}

	public String getEmail() {
		return email;
	}

	public void setEmail(String email) {
		this.email = email;
	}

	public String getLogin() {
		return login;
	}

	public void setLogin(String login) {
		this.login = login;
	}

	public List<Endereco> getEnderecos() {
		return enderecos;
	}

	public void setEnderecos(List<Endereco> enderecos) {
		this.enderecos = enderecos;
	}

}
 69  src/main/java/br/edu/fa7/clientes/model/Endereco.java 
@@ -0,0 +1,69 @@
package br.edu.fa7.clientes.model;

import java.io.Serializable;

import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;
import javax.persistence.ManyToOne;

@Entity
public class Endereco implements Serializable{

	private static final long serialVersionUID = -4335416492270530527L;

	@Id
	@GeneratedValue(strategy=GenerationType.IDENTITY)
	private Long id;

	private String logradouro;

	private String complemento;

	private String cep;

	@ManyToOne
	private Cliente cliente;

	public Long getId() {
		return id;
	}

	public void setId(Long id) {
		this.id = id;
	}

	public String getLogradouro() {
		return logradouro;
	}

	public void setLogradouro(String logradouro) {
		this.logradouro = logradouro;
	}

	public String getComplemento() {
		return complemento;
	}

	public void setComplemento(String complemento) {
		this.complemento = complemento;
	}

	public String getCep() {
		return cep;
	}

	public void setCep(String cep) {
		this.cep = cep;
	}

	public Cliente getCliente() {
		return cliente;
	}

	public void setCliente(Cliente cliente) {
		this.cliente = cliente;
	}

}
 111  src/main/java/br/edu/fa7/clientes/resources/ClienteResource.java 
@@ -0,0 +1,111 @@
package br.edu.fa7.clientes.resources;

import java.util.List;

import javax.ws.rs.Consumes;
import javax.ws.rs.DELETE;
import javax.ws.rs.GET;
import javax.ws.rs.POST;
import javax.ws.rs.PUT;
import javax.ws.rs.Path;
import javax.ws.rs.PathParam;
import javax.ws.rs.Produces;
import javax.ws.rs.core.MediaType;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.Response.Status;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;

import br.edu.fa7.clientes.model.Cliente;
import br.edu.fa7.clientes.model.Endereco;
import br.edu.fa7.clientes.service.ClienteService;

@Component
@Path("/clientes")
@Produces(MediaType.APPLICATION_JSON)
@Consumes(MediaType.APPLICATION_JSON)
public class ClienteResource {

	@Autowired
	private ClienteService service;

	@GET
	public List<Cliente> findAll() {
		List<Cliente> clientes = service.findAll();
		for(Cliente cliente : clientes) {
			removerRefereciaCirular(cliente);;
		}
		return clientes;
	}

	@GET
	@Path("{id}")
	public Response find(@PathParam("id") Long id) {
		Cliente cliente = service.find(id);
		if (cliente != null) {
			removerRefereciaCirular(cliente);
			return Response.ok(cliente).build();
		} else {
			return Response.status(Status.NOT_FOUND).build();
		}
	}

	private void removerRefereciaCirular(Cliente cliente) {
		if(cliente.getEnderecos() != null) {
			removerReferenciaCliente(cliente.getEnderecos());
		}

	}

	private void removerReferenciaCliente(List<Endereco> enderecos) {
		for(Endereco endereco : enderecos) {
			endereco.setCliente(null);
		}
	}

	@POST
	public Response save(Cliente cliente) {
		service.save(cliente);
		return Response.ok().build();
	}

	@PUT
	@Path("{id}")
	public Response update(@PathParam ("id") Long id, Cliente cliente) {
		service.update(id, cliente);
		return Response.ok().build();
	}

	@DELETE
	@Path("{id}")
	public Response delete(@PathParam ("id") Long id){
		Cliente cliente = service.find(id);
		if(cliente != null) {
			service.delete(id);
			return Response.ok().build();
		} else {
			return Response.status(Status.NOT_FOUND).build();
		}
	}

	@GET
	@Path("{id}/enderecos")
	public List<Endereco> findEnderecos(@PathParam ("id") Long id) {
		List<Endereco> enderecos = service.findEnderecosByCliente(id);
		removerReferenciaCliente(enderecos);
		return enderecos;
	}

	@GET
	@Path("{id}/enderecos/{eid}")
	public Response getEndereco(@PathParam ("id") Long id, @PathParam ("eid") Long eid) {
		Endereco endereco = service.findEnderecoByCliente(id, eid);
		if(endereco != null) {
			endereco.setCliente(null);
			return Response.ok(endereco).build();
		} else {
			return Response.status(Status.NOT_FOUND).build();
		}
	}
}
 71  src/main/java/br/edu/fa7/clientes/service/ClienteService.java 
@@ -0,0 +1,71 @@
package br.edu.fa7.clientes.service;

import java.util.List;

import javax.persistence.EntityManager;
import javax.persistence.Query;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Transactional;

import br.edu.fa7.clientes.model.Cliente;
import br.edu.fa7.clientes.model.Endereco;

@Service
public class ClienteService {

	@Autowired
	private EntityManager entityManager;

	@SuppressWarnings("unchecked")
	public List<Cliente> findAll() {
		return entityManager.createQuery("from Cliente").getResultList();
	}

	public Cliente find(Long id) {
		return entityManager.find(Cliente.class, id);
	}

	@Transactional
	public void save(Cliente cliente) {
		carregarEnderecos(cliente);
		entityManager.persist(cliente);
	}

	private void carregarEnderecos(Cliente cliente) {
		if(cliente.getEnderecos() != null) {
			for(Endereco endereco : cliente.getEnderecos()) {
				endereco.setCliente(cliente);
			}
		}
	}

	@Transactional
	public void update(Long id, Cliente cliente) {
		cliente.setId(id);
		carregarEnderecos(cliente);
		entityManager.merge(cliente);
	}

	@Transactional
	public void delete(Long id) {
		Cliente cliente = find(id);
		entityManager.remove(cliente);
	}

	@SuppressWarnings("unchecked")
	public List<Endereco> findEnderecosByCliente(Long id) {
		Query query = entityManager.createQuery("from Endereco e where e.cliente.id=:idCliente");
		query.setParameter("idCliente", id);
		return query.getResultList();
	}

	public Endereco findEnderecoByCliente(Long id, Long eid) {
		Query query = entityManager.createQuery("from Endereco e where e.cliente.id=:idCliente and e.id=:id");
		query.setParameter("idCliente", id);
		query.setParameter("id", eid);
		return (Endereco) query.getSingleResult();
	}

}
 8  src/main/resources/application.properties 
@@ -0,0 +1,8 @@
#DataSource
spring.datasource.url=jdbc:hsqldb:file:${user.home}/clientes
spring.datasource.username=sa

#JPA
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true 
