---
title: "Migration des services Web ASP.NET vers WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Migration des services Web ASP.NET vers WCF
ASP.NET fournit des bibliothèques de classes .NET Framework et des outils permettant de générer des services Web, ainsi que des fonctionnalités d'hébergement des services dans les services IIS \(Internet Information Services\).[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fournit des bibliothèques de classes .NET Framework, des outils et des fonctionnalités d'hébergement permettant aux entités logicielles de communiquer à l'aide de n'importe quel protocole, y compris ceux utilisés par les services Web.La migration des services Web ASP.NET vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permet à vos applications de tirer parti des nouvelles fonctionnalités et améliorations propres à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] offre plusieurs avantages significatifs concernant les services Web ASP.NET.Alors que les outils de services Web ASP.NET sont uniquement conçus pour générer des services Web, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit des outils qui permettent aux entités logicielles de communiquer les unes avec les autres.Cela réduira le nombre de technologies que les développeurs sont tenus de connaître pour s'adapter aux différents scénarios de communication logicielle, ce qui, en conséquence, réduira le coût des ressources de développement logiciel, ainsi que le délai de réalisation des projets de développement logiciel.  
  
 Même pour les projets de développement de services Web, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge davantage de protocoles de services Web que les services Web ASP.NET.Ces protocoles supplémentaires offrent des solutions plus sophistiquées impliquant, entre autres, des transactions et des sessions fiables.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge davantage de protocoles de transport de messages que les services Web ASP.NET.Les services Web ASP.NET prennent uniquement en charge l'envoi de messages à l'aide du protocole HTTP \(Hypertext Transfer Protocol\).[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge l'envoi de messages à l'aide de HTTP, ainsi que le protocole TCP \(Transmission Control Protocol\), les canaux nommés et Microsoft Message Queuing \(MSMQ\).Plus important, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut être étendu afin de prendre en charge d'autres protocoles de transport.Par conséquent, les logiciels développés à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent être adaptés afin de fonctionner avec une gamme plus vaste d'autres logiciels, et augmenter ainsi le retour potentiel sur investissement.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit des fonctionnalités de déploiement et de gestion des applications beaucoup plus complètes que les services Web ASP.NET.Outre un système de configuration, dont dispose également ASP.NET, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] offre un éditeur de configuration, le suivi des activités des expéditeurs aux récepteurs et via un nombre illimité d'intermédiaires, une visionneuse de suivi, la journalisation des messages, un nombre importants de compteurs de performance, et assure la prise en charge de WMI \(Windows Management Instrumentation\).  
  
 Étant donné les avantages potentiels de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] par rapport aux services Web ASP.NET, si vous utilisez, ou envisagez d'utiliser des services Web ASP.NET, vous avez plusieurs options :  
  
-   Continuer à utiliser des services Web ASP.NET et renoncer aux avantages offerts par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Continuer à utiliser des services Web ASP.NET dans l'intention d'adopter [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ultérieurement.Les rubriques de cette section expliquent comment optimiser vos chances de pouvoir utiliser les nouvelles applications de service Web ASP.NET avec les futures applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Les rubriques de cette section expliquent également comment générer de nouveaux services Web ASP.NET afin de simplifier leur migration vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Cependant, si la sécurisation des services est importante, ou que des garanties de fiabilité ou de transaction sont exigées, ou si la construction de fonctionnalités de gestion personnalisée est nécessaire, alors il est préférable d'adopter [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est spécialement conçu pour les scénarios de ce type.  
  
-   Adopter [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour un nouveau développement, tout en continuant à gérer vos applications de service Web ASP.NET existantes.Ce choix est très probablement le plus optimal.Il offre les avantages de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], tout en économisant le coût de la modification des applications existantes pour l'utiliser.Dans ce scénario, les nouvelles applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent coexister avec les applications ASP.NET existantes.Les nouvelles applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pourront utiliser les services Web ASP.NET existants, et [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permettra de programmer de nouvelles fonctionnalités opérationnelles dans les applications ASP.NET existantes du fait du mode de compatibilité ASP.NET [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Adopter [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et migrer les applications Web ASP.NET existantes vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Vous pouvez choisir cette option pour améliorer les applications existantes à l'aide des fonctionnalités fournies par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ou reproduire les fonctionnalités des services Web ASP.NET existants dans de nouvelles applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] plus performantes.  
  
> [!NOTE]
>  Soyez prudent si un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est hébergé par IIS 5.x et que ASP.NET est désinstallé.Lorsqu'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est hébergé par IIS 5.x, le code du service peut être demandé si ASP.NET est désinstallé.Lorsque ASP.NET est désinstallé sur un système d'exploitation qui exécute IIS 5.x et que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est désinstallé, un fichier avec l'extension .svc est considéré comme un fichier texte et le contenu, y compris tout code source, est retourné au demandeur.  
  
 Cette section décrit ces options en détail, compare des services Web ASP.NET à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], et fournit des instructions sur la procédure de migration du code de vos services Web ASP.NET vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## Voir aussi  
 [Anticipation de l'adoption de Windows Communication Foundation : faciliter la future migration](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)   
 [Anticipation de l'adoption de Windows Communication Foundation : faciliter l'intégration future](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)   
 [Adoption de Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)   
 [Comparaison des services Web ASP.NET et de WCF en fonction de l'objectif et des normes utilisées](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)   
 [Comparaison des services Web ASP.NET et de WCF du point de vue du développement](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)