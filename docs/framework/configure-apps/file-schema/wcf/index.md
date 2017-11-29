---
title: "Schéma de configuration WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 05aeeea7d10c012804fe083890bcc8516aa8c8bc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-configuration-schema"></a>Schéma de configuration WCF
Les éléments de configuration de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] permettent de configurer le service [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] et les applications clientes. Vous pouvez utiliser l’[outil Éditeur de configuration (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) pour créer et modifier des fichiers de configuration pour les clients et les services. Les fichiers de configuration étant au format XML, il est nécessaire de maîtriser ce format pour pouvoir modifier ces fichiers à l'aide d'un éditeur de texte, sans quoi vous risquez de rencontrer des problèmes tels qu'une balise ou un attribut d'élément XML manquant. Ce problème a lieu car les balises et les attributs d'éléments XML respectent la casse.  
  
 Le système de configuration [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] est basé sur l'espace de noms <xref:System.Configuration>. Par conséquent, vous pouvez utiliser tous les dispositifs standard fournis par l'espace de noms <xref:System.Configuration>, tel que le verrouillage, le chiffrement et la fusion de la configuration, afin de renforcer la sécurité de votre application et sa configuration. Pour plus d'informations sur ces concepts, consultez les rubriques suivantes :  
  
 [Chiffrement des informations de configuration](http://go.microsoft.com/fwlink/?LinkId=95337)  
  
 [Verrouillage des paramètres de configuration](http://go.microsoft.com/fwlink/?LinkId=95338)  
  
 Cette section décrit toutes les valeurs possibles de chaque élément de configuration et leur interaction avec d'autres éléments de configuration WCF. Le plan suivant illustre le schéma de configuration WCF.  
  
 ![Schéma de configuration WCF](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")  
  
> [!CAUTION]
>  Vous devez protéger des sections de configuration de [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] dans vos fichiers de configuration d'application (app.config) en utilisant les listes ACL appropriées, afin d'empêcher toute menace potentielle sur la sécurité.  Par exemple, vous devez vous assurer que seules les personnes appropriées peuvent accéder ou modifier les paramètres de sécurité relatifs aux liaisons d’application ou la section relative au modèle de service figurant dans le fichier de configuration d’un service.  
  
## <a name="in-this-section"></a>Dans cette section  
 [\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 Décrit l'élément `ServiceModel`.  
  
 [\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 Configure l'outil SMSvcHost.exe.  
  
 [\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 Élément de niveau supérieur permettant de définir les options lors de l'utilisation de sérialiseurs tels que le <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Configuration des applications Windows Communication Foundation](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 Explique comment configurer des services et des clients [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].
