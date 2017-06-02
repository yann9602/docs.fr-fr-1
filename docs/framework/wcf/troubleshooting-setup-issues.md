---
title: "R&#233;solution des probl&#232;mes d&#39;installation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# R&#233;solution des probl&#232;mes d&#39;installation
Cette rubrique décrit comment résoudre les problèmes d'installation de [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  
  
## Certaines clés de registre Windows Communication Foundation ne sont pas réparées par l'exécution d'une opération de réparation MSI sur le .NET Framework 3.0  
 Si vous supprimez l'une des clés de registre suivantes :  
  
-   HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\ServiceModelService 3.0.0.0  
  
-   HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\ServiceModelOperation 3.0.0.0  
  
-   HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\ServiceModelEndpoint 3.0.0.0  
  
-   HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\SMSvcHost 3.0.0.0  
  
-   HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\MSDTC Bridge 3.0.0.0  
  
 Les clés ne sont pas recréées si vous exécutez la réparation en lançant le programme d'installation du .NET Framework 3.0 à partir de l'applet **Ajout\/Suppression de programmes** située dans **Panneau de configuration**.Pour recréer ces clés correctement, l'utilisateur doit désinstaller, puis réinstaller le .NET Framework 3.0.  
  
## La corruption des services WMI bloque l'installation du fournisseur WMI Windows Communication Foundation pendant l'installation du package .NET Framework 3.0  
 La corruption des services WMI peut bloquer l'installation du fournisseur WMI Windows Communication Foundation.Pendant l'installation, le programme d'installation de Windows Communication Foundation ne peut pas enregistrer le fichier WCF .mof à l'aide du composant mofcomp.exe.La section suivante présente la liste des symptômes :  
  
1.  .NET Framework 3.0 s'installe correctement, mais le fournisseur WMI WCF n'est pas enregistré.  
  
2.  Un événement d'erreur apparaît dans le journal des événements de l'application qui référence les problèmes d'enregistrement du fournisseur WMI pour WCF, ou d'exécution du fichier mofcomp.exe.  
  
3.  Le fichier journal d'installation dd\_wcf\_retCA\* qui se trouve dans le répertoire % temp% de l'utilisateur contient des références relatives à l'échec de l'enregistrement du fournisseur WMI WCF.  
  
4.  Une exception du type de celle présentée ci\-après peut être répertoriée dans le journal des événements ou le fichier journal de suivi de l'installation :  
  
     ServiceModelReg \[11:09:59:046\] : System.ApplicationException : résultat 3 inattendu lors de l'exécution de E:\\WINDOWS\\system32\\wbem\\mofcomp.exe avec "E:\\WINDOWS\\Microsoft.NET\\Framework\\v3.0\\Windows Communication Foundation\\ServiceModel.mof"  
  
     ou :  
  
     ServiceModelReg \[07:19:33:843\] : System.TypeInitializationException : l'initialiseur de type de 'System.Management.ManagementPath' a levé une exception.\-\-\-\> System.Runtime.InteropServices.COMException \(0x80040154\) : la récupération de la fabrique de classe COM pour le composant avec le CLSID {CF4CC405\-E2C5\-4DDD\-B3CE\-5E7582D8C9FA} a échoué en raison de l'erreur suivante : 80040154.  
  
     ou :  
  
     ServiceModelReg \[07:19:32:750\] : System.IO.FileNotFoundException : impossible de charger le fichier ou l'assembly 'C:\\WINDOWS\\system32\\wbem\\mofcomp.exe' ou l'une de ses dépendances.Le système ne trouve pas le fichier spécifié.  
  
     Nom de fichier : 'C:\\WINDOWS\\system32\\wbem\\mofcomp.exe  
  
 Suivez la procédure suivante pour résoudre le problème décrit précédemment.  
  
1.  Exécutez [l'utilitaire de diagnostic WMI, version 2.0](http://go.microsoft.com/fwlink/?LinkId=94685) pour réparer le service WMI.[!INCLUDE[crabout](../../../includes/crabout-md.md)] l'utilisation de cet outil, consultez la rubrique [Utilitaire de diagnostic WMI](http://go.microsoft.com/fwlink/?LinkId=94686).  
  
 Réparez l'installation du .NET Framework 3.0 à l'aide de l'applet **Ajout\/Suppression de programmes** située dans **Panneau de configuration**, ou désinstallation\/réinstallez le .NET Framework 3.0.  
  
## La réparation du .NET Framework 3.0 après l'installation du .NET Framework 3.5 supprime les éléments de configuration introduits par le .NET Framework 3.5 dans machine.config  
 Si vous réparez le .NET Framework 3.0 après l'installation du [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], les éléments de configuration introduits par le [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] dans machine.config sont supprimés.Cependant, web.config reste intact.La solution consiste à réparer [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] par l'intermédiaire d'ARP ou à utiliser l'[Outil WorkFlow Service Registration \(WFServicesReg.exe\)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) avec le commutateur `/c`.  
  
 L'[Outil WorkFlow Service Registration \(WFServicesReg.exe\)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) se trouve à l'emplacement %windir%\\Microsoft.NET\\framework\\v3.5\\ ou %windir%\\Microsoft.NET\\framework64\\v3.5\\  
  
## Configurer IIS correctement pour WCF\/WF Webhost après l'installation du .NET Framework 3.5  
 Lorsque l'installation du [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] ne réussit pas à configurer d'autres paramètres de configuration IIS liés à [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], elle enregistre une erreur dans le journal d'installation et continue.Toute tentative d'exécution des applications WorkflowServices échoue, étant donné que les paramètres de configuration sont manquants.Par exemple, le chargement du service xoml ou de règles peut échouer.  
  
 Pour contourner ce problème, utilisez [Outil WorkFlow Service Registration \(WFServicesReg.exe\)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) avec le commutateur `/c` pour configurer correctement les mappages de scripts IIS sur l'ordinateur.L'[Outil WorkFlow Service Registration \(WFServicesReg.exe\)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) se trouve à l'emplacement %windir%\\Microsoft.NET\\framework\\v3.5\\ ou %windir%\\Microsoft.NET\\framework64\\v3.5\\  
  
## Impossible de charger le type ‘System.ServiceModel.Activation.HttpModule’ à partir de l'assembly ‘System.ServiceModel, Version 3.0.0.0, Culture\=neutral, PublicKeyToken\=b77a5c561934e089’  
 Cette erreur se produit si [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] est installé et que la fonctionnalité Activation HTTP [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)][!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est activée.Pour résoudre ce problème, exécutez la ligne de commande suivante depuis l'invite de commandes [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] :  
  
```Output  
aspnet_regiis.exe -i -enable  
```  
  
## Voir aussi  
 [Instructions d'installation](../../../docs/framework/wcf/samples/set-up-instructions.md)