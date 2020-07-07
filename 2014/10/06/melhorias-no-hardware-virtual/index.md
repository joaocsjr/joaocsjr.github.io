# Melhorias no Hardware Virtual


Com o Vsphere 5 a Vmware disponibilizou a nova versão de seu hardware Virtual, na versão 8 foram implementadas as seguintes melhorias:




 <!-- more -->




- 32 vCpus




- Virtual NUMA (vNUMA) suporte




- 1TB de memória




- Suporte a dispositivos USB 3.0




- UEFI Virtual BIOS




- Client-Connected a dispositivos USB




- Leitura de smart cards




- Non-hardware-accelerated 3D graphics for windows Aero Support - ESXi suporta graficos 3D para executar Windows com Aero e aplicações basicas em 3D.







Vsphere 5 - suporta VMs que executam versões anteriores do vmware tools e do hardware com versão 4.x, versões antigas do vmware tools são completamente suportadas no vshpere 5






<table style="font-weight:inherit;font-style:inherit;" >
<tbody style="font-weight:inherit;font-style:inherit;" >
<tr style="font-weight:inherit;font-style:inherit;" >

<td width="130" style="font-weight:inherit;font-style:inherit;" >


Versão



</td>

<td width="85" style="font-weight:inherit;font-style:inherit;" >


vSphere 4.x



</td>

<td width="85" style="font-weight:inherit;font-style:inherit;" >


vSphere 5



</td>
</tr>
<tr style="font-weight:inherit;font-style:inherit;" >

<td width="130" style="font-weight:inherit;font-style:inherit;" >


VMware Tools 4.x



</td>

<td width="85" style="font-weight:inherit;font-style:inherit;" >


Yes



</td>

<td width="85" style="font-weight:inherit;font-style:inherit;" >


Yes



</td>
</tr>
<tr style="font-weight:inherit;font-style:inherit;" >

<td width="130" style="font-weight:inherit;font-style:inherit;" >


VMware Tools 5



</td>

<td width="85" style="font-weight:inherit;font-style:inherit;" >


Yes



</td>

<td width="85" style="font-weight:inherit;font-style:inherit;" >


Yes



</td>
</tr>
<tr style="font-weight:inherit;font-style:inherit;" >

<td width="130" style="font-weight:inherit;font-style:inherit;" >


Virtual hardware



</td>

<td width="85" style="font-weight:inherit;font-style:inherit;" >


3, 4, 7



</td>

<td width="85" style="font-weight:inherit;font-style:inherit;" >


4, 7, 8



</td>
</tr>
</tbody>
</table>








Vsphere 5 Suporta OS X Server 10.6 (Snow Leopard) como guest SO quando Esxi é instalado sob o Apple Xservers.




Para que o vMotion funcione com as Vms Mac OSx, é requerido que ambos os hosts estejam instados em Apple Xserver Físico. Mac Os x 10.6 sendo executado como VM requer a versão 8 do hardware virtual que não esta disponível no Vsphere 4. É importante lembrar que VMs rodando MAC OSx não suportam a feature de Fault Tolerance (FT).


125 Views [0 Comments](https://communities.vmware.com/blogs/joaocastro/2012/09/24/melhorias-no-hardware-da-vm-no-vsphere-5#comments)

