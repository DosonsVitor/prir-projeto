## Passo a passo - Criando rede virtual com Ubuntu Server

* Iremos criar uma rede estrela com 8 VMs divididas em 4 PCs conectados por um Switch.
* Para isso tanto as VMs devem ser configuradas como as interfaces de rede dessas VMs.
* A Figura 1 ilustra a topologia de Rede

<p><center> Figura 1: Topologia de Rede estrela, com oito VMs com suas NICs em modo BRIDGE</center></p>   
   <img src="figures/star-network.png" alt=""
	title="Figura 1: Topologia de Rede Estrela" width="800" height="auto" />

### Importar VMs no VirtualBox

* O arquivo .OVA é um formato de exportação de VM utilizado pelo VirtualBox
* Vamos importar este arquivo para criar todas as VMs que precisamos para criar a nossa rede estrela.

* A Figura 2 Ilustra as configurações para a importação das VMs.

<p><center> Figura 2: Criando uma VM apartir de um arquivo OVA</center></p>   
   <img src="figures/import-ova1.png" alt=""
	title="Figura 2a: Clique em Ferramentas/Importar" width="400" height="auto"/> <br/>
   <img src="figures/import-ova2.png" alt=""
	title="Figura 2b: configurações de importação" />
