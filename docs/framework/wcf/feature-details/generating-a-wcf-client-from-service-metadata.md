---
title: "Génération d'un client WCF à partir de métadonnées de service"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27f8f545-cc44-412a-b104-617e0781b803
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9eedf84d1dccb8bc2540aca7e6bd338b4e58326d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="generating-a-wcf-client-from-service-metadata"></a>Génération d'un client WCF à partir de métadonnées de service
Cette rubrique décrit comment utiliser plusieurs commutateurs dans Svcutil.exe pour générer des clients à partir de documents de métadonnées.  
  
 Les documents de métadonnées peuvent se trouver sur un stockage durable ou être récupérés en ligne. La récupération en ligne suit le protocole WS-MetadataExchange ou le protocole Microsoft Discovery (DISCO). Svcutil.exe publie les demandes de métadonnées suivantes simultanément pour récupérer des métadonnées :  
  
-   Demande WS-MetadataExchange (MEX) à l'adresse fournie.  
  
-   Demande MEX à l'adresse fournie avec `/mex` ajouté.  
  
-   Requête DISCO (à l’aide de la [DiscoveryClientProtocol](http://go.microsoft.com/fwlink/?LinkId=94777) de services Web ASP.NET) à l’adresse fournie.  
  
 Svcutil.exe génère le client basé sur WSDL (Web Services Description Language) ou le fichier de stratégie reçu du service. Le nom d'utilisateur principal (UPN) est généré en concaténant le nom d'utilisateur avec "@" et en ajoutant ensuite un nom de domaine qualifié complet (FQDN). Toutefois, pour les utilisateurs qui sont enregistrés sur Active Directory, ce format n’est pas valid et que l’UPN de l’outil génère provoque un échec de l’authentification Kerberos avec le message d’erreur suivant : **Échec de la tentative d’ouverture de session.** Pour résoudre ce problème, résolvez manuellement le fichier client que l'outil a généré.  
  
```  
svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>  
```  
  
## <a name="referencing-and-sharing-types"></a>Référencement et partage des types  
  
|Option|Description|  
|------------|-----------------|  
|**/ reference :\<chemin d’accès >**|Référence les types contenus dans l'assembly spécifié. Lorsque vous générez des clients, utilisez cette option pour spécifier des assemblys qui peuvent contenir des types représentant les métadonnées importées.<br /><br /> Forme abrégée : `/r`|  
|**/excludeType :\<type >**|Spécifie un nom de type qualifié complet ou qualifié d'assembly à exclure des types de contrat référencés.<br /><br /> Forme abrégée : `/et`|  
  
## <a name="choosing-a-serializer"></a>Choix d'un sérialiseur  
  
|Option|Description|  
|------------|-----------------|  
|**/Serializer:auto**|Sélectionne automatiquement le sérialiseur. Cette opération utilise le sérialiseur `DataContract`. Si cela échoue, le `XmlSerializer` est utilisé.<br /><br /> Forme abrégée : `/ser:Auto`|  
|**/Serializer:DataContractSerializer**|Génère des types de données qui utilisent le sérialiseur `DataContract` pour la sérialisation et la désérialisation.<br /><br /> Forme abrégée : `/ser:DataContractSerializer`|  
|**/ Serializer : XmlSerializer**|Génère des types de données qui utilisent le `XmlSerializer` pour la sérialisation et la désérialisation.<br /><br /> Forme abrégée : `/ser:XmlSerializer`|  
|**/importXmlTypes**|Configure le sérialiseur `DataContract` pour importer les types non `DataContract` comme types `IXmlSerializable`.<br /><br /> Forme abrégée : `/ixt`|  
|**/dataContractOnly**|Génère du code pour les types `DataContract` uniquement. Les types `ServiceContract` sont générés.<br /><br /> Pour cette option, vous devez spécifier uniquement des fichiers de métadonnées locaux.<br /><br /> Forme abrégée : `/dconly`|  
  
## <a name="choosing-a-language-for-the-client"></a>Choix d'un langage pour le client  
  
|Option|Description|  
|------------|-----------------|  
|**/ Language :\<langue >**|Spécifie le langage de programmation à utiliser pour la génération de code. Spécifiez un nom de langage enregistré dans le fichier Machine.config, ou le nom qualifié complet d'une classe qui hérite de <xref:System.CodeDom.Compiler.CodeDomProvider>.<br /><br /> Valeurs : c#, cs, csharp, vb, vbs, visualbasic, vbscript, javascript, c++, mc, cpp<br /><br /> Valeur par défaut : csharp<br /><br /> Forme abrégée : `/l`<br /><br /> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Classe CodeDomProvider](http://go.microsoft.com/fwlink/?LinkId=94778).|  
  
## <a name="choosing-a-namespace-for-the-client"></a>Choix d'un espace de noms pour le client  
  
|Option|Description|  
|------------|-----------------|  
|**/ namespace :\<chaîne, chaîne >**|Spécifie un mappage d'un schéma WSDL ou XML `targetNamespace` à un espace de noms du Common Language Runtime (CLR). L'utilisation d'un caractère générique (*) pour le `targetNamespace` mappe tous les `targetNamespaces` sans mappage explicite à cet espace de noms CLR.<br /><br /> Pour vérifier que le nom de contrat du message n'entre pas en collision avec le nom d'opération, qualifiez la référence de type avec des signes deux-points doubles `::`, ou vérifiez que les noms sont uniques.<br /><br /> Valeur par défaut : dérivée de l'espace de noms cible du document de schéma pour `DataContracts`. L'espace de noms par défaut est utilisé pour tous les autres types générés.<br /><br /> Forme abrégée : `/n`|  
  
## <a name="choosing-a-data-binding"></a>Choix d’une liaison de données  
  
|Option|Description|  
|------------|-----------------|  
|**/enableDataBinding**|Implémente l'interface <xref:System.ComponentModel.INotifyPropertyChanged> sur tous les types `DataContract` pour activer la liaison de données.<br /><br /> Forme abrégée : `/edb`|  
  
## <a name="generating-configuration"></a>Génération de la configuration  
  
|Option|Description|  
|------------|-----------------|  
|**/ config :\<configFile >**|Spécifie le nom de fichier du fichier de configuration généré.<br /><br /> Valeur par défaut : output.config.|  
|**/mergeConfig**|Fusionne la configuration générée dans un fichier existant au lieu de remplacer le fichier existant.|  
|**/noconfig ignorée**|Ne génère pas de fichiers de configuration.|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des métadonnées](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Vue d’ensemble de l’architecture de métadonnées](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
