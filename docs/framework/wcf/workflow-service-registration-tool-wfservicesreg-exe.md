---
title: Outil WorkFlow Service Registration (WFServicesReg.exe)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a6a009193a88c588a19c324353296a78e27617df
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a>Outil WorkFlow Service Registration (WFServicesReg.exe)
Workflow Services Registration (WFServicesReg.exe) est un outil autonome qui peut être utilisé pour ajouter, supprimer ou réparer les éléments de configuration correspondant aux services Windows Workflow Foundation (WF).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a>Remarques  
 Cet outil se trouve à l'emplacement d'installation de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], c'est-à-dire %windir%\Microsoft.NET\Framework\v3.5 ou %windir%\Microsoft.NET\Framework64\v3.5 pour les ordinateurs 64 bits.  
  
 Les tableaux suivants décrivent les options pouvant être utilisées avec l'outil Workflow Services Registration (WFServicesReg.exe).  
  
|Option|Description|  
|------------|-----------------|  
|`/c`|Configure les services de workflow Windows. Utilisé dans les scénarios d'installation et de réparation.|  
|`/r`|Supprime la configuration des services de workflow Windows.|  
|`/v`|Imprimez des informations détaillées (pour la configuration ou la suppression).|  
|`/m`|Active le format d'enregistrement MSI.|  
|`/i`|Réduit la fenêtre lorsque l'application est exécutée.|  
  
## <a name="registration"></a>Inscription  
 L'outil vérifie le fichier Web.config et enregistre les éléments suivants :  
  
-   Assemblys de référence de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].  
  
-   Fournisseur de version pour fichiers .xoml.  
  
-   Gestionnaires HTTP pour fichiers .xoml et .rules.  
  
 L'outil vérifie le fichier Machine.config et enregistre les extensions suivantes :  
  
-   behaviorExtensions  
  
-   bindingElementExtensions  
  
-   bindingExtensions  
  
 L'outil enregistre également les importateurs de métadonnées clients suivants :  
  
-   policyImporters  
  
-   wsdlImporters  
  
 L'outil enregistre également des mappages de scripts .xoml et .rules ainsi que des gestionnaires dans la métabase IIS.  
  
 Sur les ordinateurs sous [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] et [!INCLUDE[wxp](../../../includes/wxp-md.md)] (IIS 5.1 et [!INCLUDE[iis601](../../../includes/iis601-md.md)]), un jeu de mappages de scripts .xoml et .rules est enregistré.  
  
 Sur les ordinateurs 64 bits, l'outil enregistre les mappages de scripts en mode WOW si le commutateur `Enable32BitAppOnWin64` est activé, ou les mappages de scripts 64 bits natifs si le commutateur `Enable32BitAppOnWin64` est désactivé.  
  
 Sur [!INCLUDE[wv](../../../includes/wv-md.md)] et Windows Server 2008 (IIS 7.0 et versions ultérieures) machines, deux jeux de gestionnaires .xoml et .rules sont enregistrés : un pour le mode intégré et un pour le mode classique.  
  
 Sur les ordinateurs 64 bits, trois jeux de gestionnaires sont enregistrés (indépendamment de l'état du commutateur `Enable32BitAppOnWin64`) : un pour le mode intégré, un pour le mode classique WOW et le dernier pour le mode classique 64 bits natif.  
  
> [!NOTE]
>  Contrairement à ServiceModelReg.exe, WFServicesReg.exe n'autorise pas l'ajout, la suppression ou la réparation des mappages de scripts ou des gestionnaires correspondant à un site Web particulier. Pour contourner ce problème, consultez la section « Réparation des mappages de scripts ».  
  
## <a name="usage-scenarios"></a>Scénarios d'utilisation  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a>Installation des services IIS après l'installation de .NET Framework 3.5  
 Sous [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] est installé avant les services IIS. En raison de l'indisponibilité de la métabase IIS, l'installation de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] aboutit sans installer les mappages de scripts .xoml et .rules.  
  
 Après avoir installé les services IIS, vous pouvez utiliser l'outil WFServicesReg.exe avec le commutateur `/c` pour installer ces mappages de scripts spécifiques.  
  
### <a name="repairing-the-scriptmaps"></a>Réparation des mappages de scripts  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a>Mappage de scripts supprimé sous le nœud Sites Web  
 Sous [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], le mappage de scripts .xoml ou .rules est supprimé par erreur du nœud Sites Web. Ce problème peut être résolu en exécutant l'outil WFServicesReg.exe avec le commutateur `/c`.  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a>Mappage de scripts supprimé sous un site Web particulier  
 Sous [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], un mappage de scripts .xoml ou .rules est supprimé par erreur d'un site Web particulier (celui par défaut, par exemple) et non du nœud Sites Web.  
  
 Pour réparer des gestionnaires supprimés d’un site Web particulier, vous devez exécuter « r WFServicesReg.exe » pour supprimer des gestionnaires de tous les sites Web, puis exécuter « c WFServicesReg.exe » pour créer les gestionnaires appropriés pour tous les sites Web.  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a>Configuration de gestionnaires après activation du mode IIS  
 Si les services IIS sont en mode de configuration partagé et si [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] est installé, la métabase IIS est configurée sous un emplacement partagé. Si vous basculez IIS en mode de configuration non partagé, la métabase locale ne contiendra pas les gestionnaires requis. Pour configurer la métabase locale correctement, vous pouvez importer la métabase partagée à local, soit exécuter « /c WFServicesReg.exe », qui configure la métabase locale.
