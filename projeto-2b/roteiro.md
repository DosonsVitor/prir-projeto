# Passo a passo - Criando rede virtual com Ubuntu Server

Neste roteiro/tutorial iremos auxiliar na criação de uma rede do tipo estrela com 8 servidores virtuais com o sistema operacional Ubuntu instalado. 

-----------------------------------------------------------------------------------------------------

## Súmario

### Abordagem geral
1. Objetivo
2. Topologia
3. Tabela

### Parte virtual da rede
1. Importar arquivos OVA no VirtualBox
2. Mudar hostname
3. Instalar pacotes necessários
4. Acessar o arquivo netplan
5. Editar o arquivo netplan
6. Mudar adaptador de rede no VirtualBox
7. Configurar serviço de nomes estático

### Parte física da rede
1. Conectar maquinas

### Possíveis erros

----------------------------------------------------------------------------------------------------

## Abordagem geral

### 1. Objetivo 

* O objetivo principal é criar uma rede estrela com 8 VMs divididas em 4 PCs conectados por um Switch. No fim teremos 8 servidores ubuntu conectados na mesma rede e com acesso remoto um ao outro via ssh.
* Para isso tanto as VMs devem ser configuradas como as interfaces de rede dessas VMs.

#

### 2. Topologia

* A topologia utilizada na rede é do tipo estrela, nessa topologia os computadores são todos conectados a um hub (switch) central que atua conectando todas as máquinas. O hub gerencia a transmissão de dados pela rede. Ou seja, qualquer dado enviado pela rede viaja pelo hub central antes de terminar em seu destino uqe pode ser qualquer uma das máquinas conectadas ao mesmo.
* Na nossa rede todos os 4 PCs utilizados precisam estar conectados a um switch, fazendo com que as máquinas virtuais tabém possam urilizar desta conexão caso configuradas de maneira correta conforme este guia. 
* Segue imagem da topologia da rede na figura 1.

<p><center> Figura 1: Topologia de Rede estrela, com oito VMs com suas NICs em modo BRIDGE</center></p>   
<img src="figures/star-network.svg" title="Figura 1: Topologia de Rede Estrela" width="1000" />

# 

### 3. Tabela

```
Tabela 1: Definições de endereços IPs da Rede e Nomes de Hosts
-----------------------------------------------------------------------------------------------------
|  DESCRICAO  |  IP             |   hostname        |               FQDN               |   aliase   |
-----------------------------------------------------------------------------------------------------
| VM1-PC1     | 192.168.24.33   |   srv-vm1-pc1     | dosons1.grupo3-924.ifalara.net   |   dosons   |
| VM2-PC1     | 192.168.24.34   |   srv-vm2-pc1     | dosons2.grupo3-924.ifalara.net   |   vitor    |
| VM1-PC2     | 192.168.24.35   |   srv-vm1-pc2     | clara1.grupo3-924.ifalara.net    |   clara    |
| VM2-PC2     | 192.168.24.36   |   srv-vm2-pc2     | clara2.grupo3-924.ifalara.net    |   cortez   |
| VM1-PC3     | 192.168.24.37   |   srv-vm1-pc3     | julia1.grupo3-924.ifalara.net    |   julia    |
| VM2-PC3     | 192.168.24.38   |   srv-vm2-pc3     | julia2.grupo3-924.ifalara.net    |   daniela  |
| VM1-PC4     | 192.168.24.39   |   srv-vm1-pc4     | veronica1.grupo3-924.ifalara.net |   veronica |
| VM2-PC4     | 192.168.24.40   |   srv-vm2-pc4     | veronica2.grupo3-924.ifalara.net |   nunes    |
-----------------------------------------------------------------------------------------------------
```
-----------------------------------------------------------------------------------------------------

### Importar arquivos OVA no VirtualBox

* O arquivo .OVA é um formato de exportação de VM utilizado pelo VirtualBox
* Vamos importar este arquivo para criar todas as VMs que precisamos para criar a nossa rede estrela.

* A Figura 2 Ilustra as configurações para a importação das VMs.

<p><center> Figura 2: Criando uma VM apartir de um arquivo OVA</center></p>   
   <img src="figures/import-ova1.png" alt="" 
	title="Figura 2a: Clique em Ferramentas/Importar" width="800" height="auto"/> <br/>
   <img src="figures/import-ova2.png" alt=""
	title="Figura 2c: caminho do arquivo" />
   <img src="figures/import-ova3.png" alt=""
	title="Figura 2c: configurações de importação" />	

#

### Mudar hostname
