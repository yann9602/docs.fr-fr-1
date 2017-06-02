---
title: "Conception et impl&#233;mentation de services | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "définir des contrats de service (WCF)"
ms.assetid: 036fae20-7c55-4002-b71d-ac4466e167a3
caps.latest.revision: 37
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 37
---
# Conception et impl&#233;mentation de services
Cette section contient des instructions vous permettant de définir et d'implémenter des contrats [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].Un contrat de service spécifie ce qu'un point de terminaison communique au monde extérieur.À un niveau plus concret, il s'agit d'une instruction à propos d'un ensemble de messages spécifiques organisé en modèles d'échange de messages de base, tels que les messages demande\/réponse, unidirectionnels et duplex.Si un contrat de service est un ensemble d'échanges de messages liés de manière logique, une opération de service est un échange de messages unique.Par exemple, une opération `Hello` doit évidemment accepter un message \(de sorte que l'appelant puisse annoncer la salutation\) et peut ou non retourner un message \(en fonction du niveau de courtoisie définie pour l'opération\).  
  
 Pour plus d'informations sur les contrats et autres concepts [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] fondamentaux, consultez [Concepts fondamentaux concernant Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md).Cette rubrique est consacrée au fonctionnement des contrats de service.Pour plus d'informations sur la création de clients utilisant des contrats de service pour se connecter aux services, consultez [Vue d'ensemble d'un client WCF](../../../docs/framework/wcf/wcf-client-overview.md).  
  
## Vue d'ensemble  
 Cette rubrique contient une orientation conceptuelle de niveau supérieur permettant la conception et l'implémentation de services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].Les sous\-rubriques contiennent des informations détaillées sur les particularités de ce type de conception et d'implémentation.Avant de concevoir et d'implémenter votre application [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], vous devez :  
  
-   comprendre ce qu'est un contrat de service, comment il fonctionne et comment en créer un ;  
  
-   comprendre que les contrats définissent des spécifications minimales susceptibles de ne pas être prises en charge par la configuration d'exécution et l'environnement d'hébergement.  
  
## Contrats de service  
 Un contrat de service spécifie les éléments suivants :  
  
-   les opérations qu'un contrat expose ;  
  
-   la signature des opérations en termes de messages échangés ;  
  
-   les types de données de ces messages ;  
  
-   l'emplacement des opérations ;  
  
-   les protocoles et formats de sérialisation spécifiques utilisés pour prendre en charge la communication avec le service.  
  
 Par exemple, un contrat de commande fournisseur peut avoir une opération `CreateOrder` qui accepte une entrée de types d'informations de commande et retourne des information de succès ou d'échec, y compris un identificateur de commande.Il peut également avoir une opération `GetOrderStatus` qui accepte un identificateur de commande et retourne des informations d'état de commande.Un contrat de service de cette sorte spécifierait :  
  
1.  que le contrat de commande fournisseur est composé d'opérations `CreateOrder` et `GetOrderStatus` ;  
  
2.  que les opérations auraient des messages d'entrée et des messages de sortie spécifiés ;  
  
3.  les données que ces messages pourraient transporter ;  
  
4.  des instructions catégoriques à propos de l'infrastructure de communication nécessaire pour traiter les messages avec succès.Ces informations comportent notamment les éventuelles formes de sécurité requises pour établir la communication.  
  
 Pour communiquer ce type d'informations à d'autres applications sur plusieurs plateformes \(y compris les plateformes non\-Microsoft\), les contrats de service XML sont exprimés publiquement dans des formats XML standard, tels que [Web Services Description Language](http://go.microsoft.com/fwlink/?LinkId=94952) \(WSDL\) et [XML Schema](http://go.microsoft.com/fwlink/?LinkId=94953) \(XSD\), entre autres.Les développeurs qui travaillent avec un grand nombre de plateformes différentes peuvent utiliser ces informations de contrat publiques pour créer des applications capables de communiquer avec le service, ces applications comprenant le langage des spécifications, d'une part, et ce langage assurant l'interopérabilité grâce à sa description de formes, formats et protocoles publics pris en charge par ce service, d'autre part.Pour plus d'informations sur la manière dont [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] traite ce type d'informations, consultez [Métadonnées](../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Les contrats peuvent être exprimés dans un grand nombre de langages différents et bien que WSDL et XSD constituent d'excellents langages pour décrire des services de manière accessible, ce sont des langages difficiles à utiliser directement. En outre, ils contiennent uniquement des descriptions de service et ne correspondent pas à des implémentations de contrat de service.Par conséquent, les applications [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] utilisent des attributs, des interfaces et des classes managés à la fois pour définir la structure d'un service et implémenter ce dernier.  
  
 Le contrat obtenu défini dans les types managés peut être *exporté* sous la forme de métadonnées \(WSDL et XSD\), lorsque cela est requis par les clients ou d'autres implémenteurs de service.Le résultat est un modèle de programmation simple qui peut être décrit \(à l'aide de métadonnées publiques\) à toute application cliente.Les détails des messages SOAP sous\-jacents, les informations de transport et celles relatives à la sécurité, etc., peuvent être confiés à [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], qui effectue automatiquement les conversions nécessaires entre le système de type de contrat de service et le système de type XML.  
  
 Pour plus d'informations sur la conception des contrats, consultez [Conception de contrats de service](../../../docs/framework/wcf/designing-service-contracts.md).Pour plus d'informations sur l'implémentation des contrats, consultez [Implémentation de contrats de service](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
### Messages avant et centre  
 L'utilisation d'interfaces, de classes et de méthodes managées pour modeler des opérations de service ne pose aucune difficulté dès lors que vous êtes familiarisé avec les signatures de méthode de style « appels de procédure distante » \(remote call procedure, RPC\), pour lesquelles le passage des paramètres dans les méthodes et la réception des valeurs retournées constituent le procédé standard de demande de fonctionnalités auprès d'un objet ou d'un autre type de code.Par exemple, les programmeurs qui utilisent des langages managés tels que [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] et C\+\+ COM peuvent appliquer leur connaissance de l'approche RPC \(qu'ils utilisent des objets ou des interfaces\) à la création de contrats de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et ne pas rencontrer les problèmes inhérents aux systèmes d'objets distribués RPC.La programmation orientée service présente les mêmes avantages que la programmation orientée message faiblement couplée tout en permettant aux développeurs de continuer à bénéficier de la convivialité de la programmation RPC.  
  
 De nombreux programmeurs préfèrent les interfaces de programmation d'application orientées message, telles que les files d'attente de messages comme Microsoft MSMQ, les espaces de noms <xref:System.Messaging> dans le .NET Framework ou l'envoi sous forme de langage XML non structuré dans les requêtes HTTP, pour n'en nommer que quelques\-unes.Pour plus d'informations sur la programmation de niveau message, consultez [Utilisation de contrats de message](../../../docs/framework/wcf/feature-details/using-message-contracts.md), [Programmation de service au niveau du canal](../../../docs/framework/wcf/extending/service-channel-level-programming.md) et [Interopérabilité avec les applications POX](../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### Fonctionnement de la hiérarchie des spécifications  
 Un contrat de service regroupe les opérations, spécifie le modèle d'échange de messages, les types de messages et les types de données transportés par ces messages et indique les catégories de comportements que l'implémentation doit pouvoir adopter en cours d'exécution pour assurer la prise en charge du contrat \(il peut, par exemple, s'agir des comportements en matière de chiffrement et de signature des messages\).Le contrat de service proprement dit ne spécifie pas précisément comment ces spécifications sont satisfaites, mais uniquement qu'elles doivent l'être.Le type de chiffrement ou la manière dont un message doit être signé incombent à l'implémentation et à la configuration des services concernés.  
  
 Remarquez la façon dont le contrat requiert certaines choses de l'implémentation de contrat de service et de la configuration à l'exécution pour ajouter un comportement.L'ensemble de spécifications qui doivent être satisfaites pour exposer un service pour une utilisation repose sur l'ensemble de spécifications précédent.Si un contrat spécifie des exigences concernant l'implémentation, une implémentation peut requérir une plus grande partie de la configuration et des liaisons qui autorisent l'exécution du service.Pour finir, l'application hôte doit également prendre en charge les spécifications ajoutées par la configuration du service et les liaisons.  
  
 N'oubliez pas ces spécifications supplémentaires lors de la conception, de l'implémentation, de la configuration et de l'hébergement d'une application de service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].Par exemple le contrat peut spécifier qu'il doit prendre en charge une session.Dans un tel cas, vous devez configurer la liaison de sorte à permettre la prise en charge de cette spécification contractuelle, sinon l'implémentation de service ne fonctionnera pas.Si votre service requiert l'authentification intégrée Windows \(Windows Integrated Authentification, WIA\) et qu'il est hébergé par les services IIS, l'option WIA de l'application Web dans laquelle se trouve le service doit être activée et l'option de prise en charge anonyme doit être désactivée.Pour plus d'informations sur les fonctionnalités ainsi que sur les répercussions des différents types d'applications pouvant héberger des services, consultez [Hébergement de services](../../../docs/framework/wcf/hosting-services.md).  
  
## Voir aussi  
 [Conception de contrats de service](../../../docs/framework/wcf/designing-service-contracts.md)   
 [Implémentation de contrats de service](../../../docs/framework/wcf/implementing-service-contracts.md)