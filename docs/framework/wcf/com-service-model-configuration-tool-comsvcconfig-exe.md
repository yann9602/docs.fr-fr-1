---
title: "Outil de configuration de modèle de service COM+ (ComSvcConfig.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3f812beea611633fe1fa47ced5db46c462443f28
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a>Outil de configuration de modèle de service COM+ (ComSvcConfig.exe)
L'outil en ligne de configuration de modèle de service COM+ (ComSvcConfig.exe) permet de configurer des interfaces COM+ à exposer en tant que services Web.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a>Remarques  
  
> [!NOTE]
>  Vous devez être administrateur sur l'ordinateur local pour pouvoir utiliser ComSvcConfig.exe.  
  
 Cet outil se trouve à l'emplacement suivant :  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
 Pour plus d’informations sur ComSvcConfig.exe, consultez [Comment : utiliser COM + Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
 Le tableau suivant décrit les modes qui peuvent être utilisés avec ComSvcConfig.exe.  
  
|Option|Description|  
|------------|-----------------|  
|`install`|Installe une configuration d'interface COM+ pour l'intégration du modèle de service.<br /><br /> Forme abrégée : `/i`.|  
|`uninstall`|Désinstalle une configuration d'interface COM+ de l'intégration de modèle de service.<br /><br /> Forme abrégée : `/u`.|  
|`list`|Répertorie les informations relatives aux applications COM+ et aux composants qui possèdent des interfaces configurées pour l'intégration de modèle de service.<br /><br /> Forme abrégée : `/l`.|  
  
 Le tableau suivant décrit les indicateurs qui peuvent être utilisés avec ComSvcConfig.exe.  
  
|Option|Description|  
|------------|-----------------|  
|`/application:`\< *ApplicationID* &#124; *ApplicationName*\>|Spécifie l'application COM+ à configurer.<br /><br /> Forme abrégée : `/a`.|  
|`/contract:`\< *ClassID* &#124; *ProgID* &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124;\*\>|Spécifie le composant et l'interface COM+ qui seront configurés en tant que contrat pour le service.<br /><br /> Forme abrégée : `/c`.<br /><br /> Alors que le caractère générique (\*) peut être utilisé lorsque vous spécifiez les noms de composant et d’interface, nous recommandons que vous ne l’utilisez pas, car vous pouvez exposer les interfaces que vous ne souhaitez pas.|  
|`/hosting:`\< *complus* &#124; *a été*\>|Spécifie s'il faut utiliser le mode d'hébergement COM+ ou Web.<br /><br /> Forme abrégée : `/h`.<br /><br /> L'utilisation du mode d'hébergement COM+ requiert l'activation explicite de l'application COM+. L'utilisation du mode d'hébergement Web permet à l'application COM+ d'être activée automatiquement, de façon appropriée. Si l'application COM+ est une application de bibliothèque, elle s'exécute au cours du processus de Services Internet (IIS). Si l'application COM+ est une application serveur, elle s'exécute au cours du processus Dllhost.exe.|  
|`/webSite:`\< *WebsiteName*\>|Spécifie le site Web à utiliser pour l'hébergement lorsque le mode d'hébergement Web est utilisé (consultez l'indicateur `/hosting` ).<br /><br /> Forme abrégée : `/w`.<br /><br /> Si aucun site web n’est spécifié, le site web par défaut est utilisé.|  
|`/webDirectory:`\< *WebDirectoryName*\>|Spécifie le répertoire virtuel à utiliser pour l'hébergement lorsque le mode d'hébergement Web est utilisé (consultez l'indicateur `/hosting` ).<br /><br /> Forme abrégée : `/d`.|  
|`/mex`|Ajoute un service d'échange de métadonnées (MEX, Metadata Exchange) à la configuration du service par défaut pour prendre en charge les clients qui souhaitent récupérer une définition de contrat à partir du service.<br /><br /> Forme abrégée : `/x`.|  
|`/id`|Affiche les informations sur l'application, le composant et l'interface en tant qu'ID.<br /><br /> Forme abrégée : `/k`.|  
|`/nologo`|Empêche ComSvcConfig.exe d'afficher son logo.<br /><br /> Forme abrégée : `/n`.|  
|`/verbose`|Affiche tous les avertissements ou tout le texte informatif en plus des erreurs rencontrées.<br /><br /> Forme abrégée : `/v`.|  
|`/help`|Affiche le message d'utilisation.<br /><br /> Forme abrégée : `/?`.|  
|`/partial`|Génère une configuration de service lorsque l'interface spécifiée inclut une ou plusieurs signatures de méthode qui peuvent être exposées. Au moment de l'initialisation, les méthodes compatibles apparaissent en tant qu'opérations sur le contrat de service, et les méthodes non compatibles sont ignorées et absentes du contrat de service.<br /><br /> Si cet indicateur est manquant, l'outil ne génère pas de configuration de service lorsque l'interface spécifiée inclut une ou plusieurs méthodes incompatibles.|  
  
## <a name="examples"></a>Exemples  
  
### <a name="description"></a>Description  
 L'exemple suivant ajoute l'interface `IFinances` du composant `ItemOrders.IFinancial` (de l'application COM+ OnlineStore) aux interfaces exposées en tant que services Web, à l'aide du mode d'hébergement COM+. Outre les erreurs rencontrées, l'affichage inclut tous les avertissements.  
  
### <a name="code"></a>Code  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a>Description  
 L'exemple suivant illustre l'ajout de l'interface `IStockLevels` du composant `ItemInventory.Warehouse` (de l'application COM+ OnlineWarehouse) aux interfaces exposées en tant que services Web, à l'aide du mode d'hébergement Web. Le service Web est en mode d'hébergement Web dans le répertoire virtuel OnlineWarehouse d'IIS.  
  
### <a name="code"></a>Code  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a>Description  
 L'exemple suivant illustre la suppression de l'interface `IFinances` du composant `ItemOrders.Financial` (de l'application COM+ OnlineStore) du groupe d'interfaces exposées en tant que services Web.  
  
### <a name="code"></a>Code  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a>Description  
 L'exemple suivant répertoire les interfaces actuellement exposées, hébergées par COM+, ainsi que l'adresse correspondante et les détails de liaison, pour l'application COM+ OnlineStore située sur l'ordinateur local.  
  
### <a name="code"></a>Code  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : utiliser l’outil de Configuration de modèle de Service COM +](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
