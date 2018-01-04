---
title: Gestion des erreurs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 29ae7505f3fcd460abe9e65974f564a296723aa1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="error-handling"></a>Gestion des erreurs
## <a name="error-handling-in-windows-communication-foundation"></a>Gestion des erreurs dans Windows Communication Foundation  
 Lorsqu'un service rencontre une exception ou une erreur inattendue, il existe plusieurs manières de concevoir une solution de gestion des exceptions. Il n’existe aucun unique « correct » ou « meilleures pratiques » gestion des erreurs solution, il existe plusieurs chemins valides à prendre en compte. Il est recommandé d’implémenter une solution hybride qui combine plusieurs approches de la liste ci-dessous, selon la complexité de l’implémentation de WCF, le type et la fréquence des exceptions, le texte gérées par rapport à la nature non gérée de la exceptions et de suivi associé, enregistrement ou exigences de la stratégie.  
  
 Ces solutions sont expliquées plus en détail dans le reste de cette section.  
  
### <a name="the-microsoft-enterprise-library"></a>Microsoft Enterprise Library  
 Le bloc d'application de gestion des exceptions Microsoft Enterprise Library permet d'implémenter des modèles communs de conception et de créer une stratégie cohérente de traitement des exceptions qui se produisent dans toutes les couches de l'architecture d'une application d'entreprise. Il est conçu pour prendre en charge le code spécifique contenu dans les instructions catch des composants de l'application. Au lieu de répéter ce code (par exemple le code qui stocke les informations sur l'exception) dans des blocs catch identiques d'une application, le bloc d'application de gestion des exceptions permet aux développeurs d'encapsuler cette logique comme gestionnaires d'exceptions réutilisables.  
  
 Cette bibliothèque comprend un gestionnaire d'exceptions du contrat d'erreur prêt à l'emploi. Ce gestionnaire d'exceptions est conçu pour une utilisation aux limites du service Windows® Communication Foundation (WCF) et génère un nouveau contrat d'erreur à partir de l'exception.  
  
 Les blocs d'application visent à incorporer les meilleures pratiques fréquemment utilisées et à fournir une approche commune pour la gestion des exceptions dans votre application. D'autre part, les gestionnaires d'erreurs personnalisés et les contrats d'erreur développés s'avèrent également très utiles. Par exemple, les gestionnaires d’erreurs personnalisés offrent la possibilité de promouvoir automatiquement toutes les exceptions en FaultExceptions et également ajouter des fonctionnalités de journalisation à votre application.  
  
 Pour plus d’informations, consultez [Microsoft Enterprise Library](http://msdn.microsoft.com/library/ff632023.aspx).  
  
### <a name="dealing-with-expected-exceptions"></a>Traiter les exceptions attendues  
 Le plan d’action approprié consiste à intercepter des exceptions attendues dans chaque opération ou d’un point d’extensibilité concerné, à déterminer s’ils peuvent être récupérées à partir d’et retournent l’erreur personnalisée appropriée dans un FaultException\<T >  
  
### <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a>Traiter les exceptions inattendues à l'aide d'un IErrorHandler  
 Pour gérer des exceptions inattendues, l’action recommandée est « connecter » un IErrorHandler. Gestionnaires d’erreurs uniquement interceptent des exceptions au niveau du runtime WCF (la couche « modèle de service »), pas au niveau de la couche de canal. La seule manière de connecter un IErrorHandler au niveau de canal consiste à créer un canal personnalisé, ce qui est déconseillé dans la plupart des scénarios.  
  
 Une exception « inattendue » n’est généralement ni une exception irrécupérable ni une exception de traitement ; Il est à la place, une exception utilisateur inattendue. Une exception irrécupérable (par exemple, une exception de mémoire insuffisante) – généralement gérée par le [Gestionnaire d’exceptions de modèle de Service](http://msdn.microsoft.com/library/system.servicemodel.dispatcher.exceptionhandler.aspx) – ne peut généralement être gérées automatiquement en douceur et la seule raison de gérer cette exception tout est peut-être effectuer un enregistrement supplémentaire ou pour retourner une exception standard au client. Une exception de traitement se produit dans le traitement du message (par exemple, au niveau de la sérialisation, de l'encodeur ou du formateur), généralement elle ne peut pas être gérée dans un IErrorHandler, car il est trop tôt ou trop tard pour que le gestionnaire d'erreurs intervienne lorsque ces exceptions se produisent. De même, les exceptions de transport ne peuvent pas être gérées dans un IErrorHandler.  
  
 Avec un IErrorHandler, vous pouvez explicitement contrôler le comportement de votre application lorsqu'une exception est levée. Vous pouvez :  
  
1.  Déterminer s'il faut ou non envoyer une erreur au client  
  
2.  Remplacer une exception par une erreur  
  
3.  Remplacer une erreur par une autre  
  
4.  Effectuer l'enregistrement ou le suivi  
  
5.  Exécuter d'autres activités personnalisées  
  
 Pour installer un gestionnaire d'erreurs personnalisé, ajoutez-le à la propriété ErrorHandlers des répartiteurs de canal de votre service.  Il est possible d'avoir plusieurs gestionnaire d'erreurs et ils sont appelés dans l'ordre où ils sont ajoutés à cette collection.  
  
 IErrorHandler.ProvideFault contrôle le message d'erreur qui est envoyé au client. Cette méthode est appelée quel que soit le type de l'exception levée par une opération dans votre service. Si aucune opération n'est effectuée ici, WCF suppose le comportement par défaut et continue comme si aucun gestionnaire d'erreurs personnalisé n'était installé.  
  
 Un domaine dans lequel vous pouvez adopter cette approche est lorsque vous souhaitez créer une place centrale de conversion des exceptions en erreurs avant qu'elles ne soient envoyées au client (en veillant à ce que l'instance ne soit pas supprimée et le canal déplacé vers l'état d'erreur).  
  
 La méthode IErrorHandler.HandleError est généralement utilisée pour implémenter des comportements d'erreur tels que l'enregistrement des erreurs, les notifications système, la fermeture de l'application, etc. IErrorHandler.HandleError peut être appelée à plusieurs endroits dans le service, et selon l'endroit où l'erreur est retournée, la méthode HandleError peut ou non être appelée par le thread même que l'opération ; aucune garantie n'est donnée à cet égard.  
  
### <a name="dealing-with-exceptions-outside-wcf"></a>Traiter les exceptions en dehors de WCF  
 Souvent, des exceptions de configuration, des exceptions de chaîne de connexion à la base de données, et d'autres exceptions similaires peuvent se produire dans le contexte d'une application WCF, mais elles ne sont pas des exceptions provoquées par le modèle de service ou le service Web. Ces exceptions sont des exceptions « standard » externes au service web et doivent être gérées comme les autres exceptions externes dans l’environnement à gérer.  
  
### <a name="tracing-exceptions"></a>Suivi d'exceptions  
 Le traçage est le lieu uniquement « fourre-tout » où vous pouvez afficher toutes les exceptions. Pour plus d'informations sur le suivi et l'enregistrement des exceptions, consultez Suivi et enregistrement.  
  
### <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a>Erreurs de modèle d'URI lors de l'utilisation de WebGetAttribute et WebInvokeAttribute  
 Les attributs WebGet et WebInvoke vous permettent de spécifier un modèle d'URI qui mappe les composants de l'adresse de requête aux paramètres d'opération. Par exemple, le modèle d'URI « weather/{state}/{city} » mappe l'adresse de requête dans les jetons de littéraux, un état de paramètre nommé et un paramètre nommé city. Ces paramètres peuvent être liés par nom à certains des paramètres formels de l'opération.  
  
 Les paramètres de modèle s'affichent au format de chaînes dans l'URI et les paramètres formels d'un contrat typé peuvent être des types non-chaînes. Par conséquent, une conversion doit avoir lieu avant que l'opération puisse être appelée. A [table des formats de conversion](http://msdn.microsoft.com/library/bb412172.aspx) est disponible.  
  
 Cependant, si la conversion échoue, il n'existe aucun moyen d'indiquer à l'opération qu'une erreur s'est produite. Conversion de type plutôt que de surfaces sous la forme d'un échec de distribution.  
  
 Une erreur de distribution de conversion de type peut être inspectée de la même façon que d'autres types d'erreurs de distribution en installant un gestionnaire d'erreurs. Le point d'extensibilité d'IErrorHandler est appelé pour gérer les exceptions au niveau de service. À partir de là, choisissez la réponse à renvoyer à l’appelant, et effectuez des tâches et des rapports personnalisés.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs WCF de base](http://msdn.microsoft.com/library/gg281715.aspx)
