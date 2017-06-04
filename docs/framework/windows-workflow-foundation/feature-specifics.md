---
title: "Fonctionnalit&#233;s sp&#233;cifiques &#224; Windows Workflow Foundation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Fonctionnalit&#233;s sp&#233;cifiques &#224; Windows Workflow Foundation
[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] ajoute un certain nombre de fonctionnalités à Windows Workflow Foundation.Ce document décrit quelques\-unes de ces nouvelles fonctionnalités et donne des détails relatifs à certains scénarios dans lesquels elles peuvent être utiles.  
  
## Activités de messagerie  
 Les activités de messagerie \(<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.ReceiveReply>\) permettent d'envoyer et de recevoir des messages [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] à partir de votre flux de travail. Les activités <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> servent à former une opération de service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] qui est exposée via WSDL, à l'instar des services Web standard [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.ReceiveReply> permettent d'utiliser un service Web similaire à un <xref:System.ServiceModel.ChannelFactory> WCF ; il existe également une option **Ajouter une référence de service** pour Workflow Foundation qui génère des activités préconfigurées.  
  
### Activités de messagerie \- Mise en route  
  
-   Dans [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], créez un projet d'application de service de flux de travail WCF.Une combinaison <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> sera placée sur votre zone de dessin.  
  
-   Cliquez avec le bouton droit de la souris sur le projet et sélectionnez **Ajouter une référence de service**. Pointez vers un WSDL de service Web existant et cliquez sur **OK**. Générez votre projet afin d'afficher les activités générées \(implémentées à l'aide de <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.ReceiveReply>\) dans votre boîte à outils.  
  
-   Vous trouverez des exemples de telles activités dans les sections suivantes :  
  
    -   Informations de base : [Services](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Scénarios : [Services](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
-   [Documentation conceptuelle](http://go.microsoft.com/fwlink/?LinkId=204801)  
  
-   [Documentation relative au concepteur d'activités de messagerie](http://go.microsoft.com/fwlink/?LinkId=204802)  
  
### Exemple de scénario d'activités de messagerie  
 Un service `BestPriceFinder` appelle plusieurs services de compagnies aériennes afin de trouver le tarif le plus intéressant pour un itinéraire particulier. L'implémentation de ce scénario nécessiterait normalement l'utilisation d'activités de messagerie afin de recevoir la demande de prix, de récupérer les tarifs à partir des services principaux et de répondre à la demande de prix en indiquant le meilleur tarif. Cela nécessiterait également le recours à des activités prédéfinies afin de créer la logique métier pour calculer le meilleur tarif.  
  
## WorkflowServiceHost  
 Le <xref:System.ServiceModel.WorkflowServiceHost> est l'hôte de flux de travail prédéfini qui prend en charge plusieurs instances, la configuration et la messagerie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] \(bien que les flux de travail ne soient pas nécessaires pour utiliser la messagerie en vue de l'hébergement\). Il intègre également les fonctionnalités de persistance, de suivi et de contrôle d'instance via un ensemble de comportements de service. Tout comme le <xref:System.ServiceModel.ServiceHost> de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], le <xref:System.ServiceModel.WorkflowServiceHost> peut être auto\-hébergé dans une console\/application WPF\/WinForms ou un service Windows, ou être hébergé sur le Web \(en tant que fichier .xamlx\) dans IIS ou WAS.  
  
### Mise en route avec l'hôte du service de workflow  
  
-   Dans Visual Studio 2010, créez un projet d'application de service de flux de travail [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] : ce projet sera configuré pour permettre l'utilisation de <xref:System.ServiceModel.WorkflowServiceHost> dans un environnement d'hôte sur le Web.  
  
-   Pour héberger un flux de travail sans rapport avec la messagerie, ajoutez un <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> personnalisé qui créera l'instance en fonction d'un message.  
  
-   Il est possible de contrôler des instances de flux de travail \(de lessuspendre ou de les arrêter, par exemple\) en ajoutant un <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> au <xref:System.ServiceModel.WorkflowServiceHost>, puis en utilisant un <xref:System.ServiceModel.Activities.WorkflowControlClient>.  
  
-   Vous trouverez des exemples de <xref:System.ServiceModel.WorkflowServiceHost> dans les sections suivantes :  
  
    -   [Exécution](../../../docs/framework/windows-workflow-foundation/samples/execution.md)  
  
    -   Informations de base : [Services](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Scénarios : [Services](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Application : [Gestion de l'instance interrompue](../../../docs/framework/windows-workflow-foundation/samples/suspended-instance-management.md)  
  
-   [Documentation conceptuelle relative à WorkflowServiceHost](http://go.microsoft.com/fwlink/?LinkId=204807)  
  
### Scénario WorkflowServiceHost  
 Un service BestPriceFinder appelle plusieurs services de compagnies aériennes afin de trouver le tarif le plus intéressant pour un itinéraire particulier. L'implémentation de ce scénario nécessiterait normalement l'hébergement du flux de travail dans <xref:System.ServiceModel.WorkflowServiceHost>. Cela nécessiterait également le recours à des activités de messagerie afin de recevoir la demande de prix, de récupérer les tarifs à partir des services principaux et de répondre à la demande de prix en indiquant le meilleur tarif.  
  
## Corrélation  
 Une corrélation correspond à l'un des deux concepts suivants :  
  
-   manière de regrouper des messages ; autrement dit, la relation entre un message de demande et sa réponse ;  
  
-   manière de mapper des données à une instance de service.  
  
### Mise en route  
  
-   Pour démarrer une corrélation, créez un projet dans Visual Studio.Créez une variable de type <xref:System.ServiceModel.Activities.CorrelationHandle>.  
  
-   À titre d'exemple de corrélation utilisé pour regrouper des messages, citons une corrélation demande\-réponse.  
  
    -   Dans une activité <xref:System.ServiceModel.Activities.Receive>, cliquez sur la propriété <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> et ajoutez un <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> à l'aide du CorrelationHandle créé à la première étape décrite précédemment.  
  
    -   Créez une activité <xref:System.ServiceModel.Activities.SendReply> en cliquant avec le bouton droit sur <xref:System.ServiceModel.Activities.Receive> puis en sélectionnant « Create SendReply ».Collez\-la dans votre flux de travail à la suite de l'activité <xref:System.ServiceModel.Activities.Receive>.  
  
-   Une corrélation basée sur le contenu qui mappe des données \(un numéro de commande, par exemple\) à une instance de flux de travail particulière constitue un exemple de mappage de données à une instance de service.  
  
    -   Dans une activité de messagerie, cliquez sur la propriété `CorrelationInitializers` et ajoutez un <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> à l'aide de la variable <xref:System.ServiceModel.Activities.CorrelationHandle> créée ci\-dessus.Double\-cliquez sur la propriété de votre choix dans le message \(par exemple,OrderID\) dans le menu déroulant.Définissez la propriété `CorrelatesWith` avec la variable <xref:System.ServiceModel.Activities.CorrelationHandle> utilisée précédemment.  
  
-   Exemples :  
  
    -   Informations de base : [Services](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   Scénarios : [Services](../../../docs/framework/windows-workflow-foundation/samples/services.md)  
  
    -   [Documentation conceptuelle relative à la corrélation](http://go.microsoft.com/fwlink/?LinkId=204939)  
  
### Scénario de corrélation  
 Un flux de travail de traitement des commandes est utilisé pour gérer la création de nouvelles commandes et mettre à jour les commandes figurant déjà dans le processus. L'implémentation de ce scénario nécessiterait normalement l'hébergement du flux de travail dans <xref:System.ServiceModel.WorkflowServiceHost> et le recours à des activités de messagerie. Cela impliquerait également une corrélation basée sur `orderId` pour vérifier que les mises à jour sont effectuées dans le flux de travail approprié.  
  
## Configuration simplifiée  
 Le schéma de configuration [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est complexe et propose des fonctionnalités difficiles à trouver par les utilisateurs.Dans [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], nous nous sommes attachés à aider les utilisateurs de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] lorsqu'ils configurent leurs services avec les fonctionnalités suivantes :  
  
-   Plus besoin de configuration explicite par service.Si vous ne configurez pas d'éléments pour votre \<service\> et que votre service ne définit aucun point de terminaison par programme, un jeu de points de terminaison est automatiquement ajouté à votre service : un pour chaque adresse de base de service et pour chaque contrat implémenté par votre service.  
  
-   Permet à l'utilisateur de définir pour les comportements et les liaisons WCF des valeurs par défaut qui seront appliquées aux services sans configuration explicite.  
  
-   Les points de terminaison standard définissent les points de terminaison préconfigurés réutilisables qui ont des valeurs fixes pour une ou plusieurs propriétés de point de terminaison \(adresse, liaison ou contrat\) et permettent la définition de propriétés personnalisées.  
  
-   Enfin, le <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> permet d'effectuer la gestion centralisée de la configuration du client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], ce qui est utile dans les cas où une configuration est sélectionnée ou modifiée après le chargement du domaine d'application.  
  
### Mise en route  
  
-   [Guide du développeur pour WCF 4.0](http://go.microsoft.com/fwlink/?LinkId=204940)  
  
-   [Configuration Channel Factory](http://go.microsoft.com/fwlink/?LinkId=204941)  
  
-   [Élément de point de terminaison standard](http://go.microsoft.com/fwlink/?LinkId=204942)  
  
-   [Améliorations apportées à la configuration de service dans .Net Framework 4](http://go.microsoft.com/fwlink/?LinkId=204943)  
  
-   [Erreur souvent commise par les utilisateurs dans .NET 4 : entrée incorrecte du nom de configuration du service WF\/WCF](http://go.microsoft.com/fwlink/?LinkId=204944)  
  
### Scénarios de configuration simplifiée  
  
-   Un développeur ASMX expérimenté souhaite commencer à utiliser [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].Toutefois, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] lui semble trop compliqué \!Quelles sont les informations dont j'ai besoin pour écrire dans un fichier de configuration ?Dans .NET 4, vous pouvez même décider de ne pas avoir de fichier de configuration du tout.  
  
-   Il est très difficile de configurer et de gérer un ensemble existant de services WCF.Le fichier de configuration contient des milliers de lignes de code XML qui doivent être manipulées avec la plus grande prudence.De l'aide est nécessaire pour réduire la quantité de code afin que ce dernier soit plus facile à gérer.  
  
## Programme de résolution de contrat de données  
 Dans .NET 3.5, il existait quelques limitations à la conception de types connus :  
  
-   L'ajout de types connus de manière dynamique pendant la sérialisation ou la désérialisation était impossible.  
  
-   Les sérialiseurs n'étaient pas en mesure de gérer des informations xsi:type inconnues.  
  
-   Il n'était pas possible pour les utilisateurs de spécifier le xsi:type qu'ils souhaitaient voir apparaître sur le câble pour, par exemple, réduire la taille d'une instance de sérialisation sur ce dernier.  
  
 Le [DataContractResolver](../../../docs/framework/wcf/samples/datacontractresolver.md) apporte une réponse à ces questions dans la version .NET 4.5.  
  
### Mise en route  
  
-   [Documentation relative à l'API d'un programme de résolution de contrat de données](http://go.microsoft.com/fwlink/?LinkId=204946)  
  
-   [Présentation du programme de résolution de contrat de données](http://go.microsoft.com/fwlink/?LinkId=204947)  
  
-   Exemples :  
  
    -   [DataContractResolver](../../../docs/framework/wcf/samples/datacontractresolver.md)  
  
    -   [KnownAssemblyAttribute](../../../docs/framework/wcf/samples/knownassemblyattribute.md)  
  
### Scénarios d'un programme de résolution de contrat de données  
  
-   Éviter d'avoir à déclarer des dizaines d'objets <xref:System.Runtime.Serialization.KnownTypeAttribute> dans un service.  
  
-   Réduire la taille d'un objet BLOB XML.  
  
## Organigramme  
 Un organigramme est un paradigme connu permettant la représentation visuelle de problèmes liés à un domaine.Il s'agit d'un nouveau style de flux de contrôle qui a été introduit dans .NET 4.La principale caractéristique d'un organigramme tient dans le fait qu'une seule activité est exécutée à un moment donné.Les organigrammes peuvent représenter des boucles et des alternatives possibles, mais ne peuvent pas, de manière native, représenter l'exécution simultanée de plusieurs nœuds.  
  
### Mise en route  
  
-   Dans [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], créez une application console de workflowAjoutez un organigramme dans le concepteur de workflow.  
  
-   La fonctionnalité d'organigramme utilise les classes suivantes :  
  
    -   <xref:System.Activities.Statements.Flowchart>  
  
    -   <xref:System.Activities.Statements.FlowNode>  
  
    -   <xref:System.Activities.Statements.FlowDecision>  
  
    -   <xref:System.Activities.Statements.FlowStep>  
  
    -   <xref:System.Activities.Statements.FlowSwitch%601>  
  
-   Exemples :  
  
    -   [Gestion des erreurs dans une activité Flowchart à l'aide de TryCatch](../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
  
    -   [Scénario StateMachine à l'aide d'une combinaison de FlowChart et de Pick](../../../docs/framework/windows-workflow-foundation/samples/statemachine-scenario-using-a-combination-of-flowchart-and-pick.md)  
  
    -   [Processus d'embauche](../../../docs/framework/windows-workflow-foundation/samples/hiring-process.md)  
  
-   Documentation relative au concepteur :  
  
    -   [Concepteurs d'activités d'organigramme](../Topic/Flowchart%20Activity%20Designers.md)  
  
### Scénarios d'organigramme  
 Une activité d'organigramme peut permettre d'implémenter un jeu de devinette.Le jeu de devinette est très simple : l'ordinateur sélectionne un nombre aléatoire et le joueur doit deviner ce nombre.Au moment où le joueur fait une proposition, l'ordinateur lui donne un indice \(par exemple,« essayez un nombre inférieur »\).Si le joueur devine le nombre en moins de 7 tentatives, il reçoit un message de félicitations spécial de l'ordinateur.Ce jeu peut être implémenté avec une combinaison des activités procédurales suivantes :  
  
-   <xref:System.Activities.Statements.Sequence>  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.TryCatch>  
  
-   <xref:System.Activities.Statements.Assign%601>  
  
-   <xref:System.Activities.Statements.If>  
  
## Activités procédurales \(Sequence, If, ForEach, Switch, Assign, DoWhile, While\)  
 Les activités procédurales fournissent un mécanisme de modélisation d'un flux de contrôle séquentiel en faisant appel à des concepts que connaissent bien les programmeurs.Ces activités permettent les constructions de langage de programmation structurées de manière traditionnelle et, lorsque cela s'avère nécessaire, une parité de langages avec les langages procéduraux courants, tels que C\#\/VB.  
  
### Mise en route  
  
-   Dans [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], créez une application console de workflow.Ajoutez des activités procédurales dans le concepteur de workfow.  
  
-   Exemples :  
  
    -   [Processus d'embauche](../../../docs/framework/windows-workflow-foundation/samples/hiring-process.md)  
  
    -   [Processus d'achat d'entreprise](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md)  
  
-   Documentation relative au concepteur :  
  
    -   [Concepteur d'activités Parallel](../Topic/Parallel%20Activity%20Designer.md)  
  
    -   [Concepteur d'activités ParallelForEach\<T\>](../Topic/ParallelForEach%3CT%3E%20Activity%20Designer.md)  
  
### Scénarios d'activités procédurales  
  
-   <xref:System.Activities.Statements.Parallel>Parallèle : un système de gestion documentaire intranet dispose d'un flux de travail d'approbation des documents.Les documents doivent être approuvés par du personnel travaillant dans plusieurs services différents avant d'être publiés sur le réseau intranet.Aucun ordre d'approbation n'est établi ; l'approbation peut avoir lieu à tout moment, tant que le document se trouve en phase d'attente d'approbation.Lorsqu'un utilisateur soumet un document à des fins de révision, ce dernier doit être approuvé par son supérieur hiérarchique direct, par l'administrateur de l'intranet et par le responsable de la communication interne.  
  
-   <xref:System.Activities.Statements.ParallelForEach%601> : une application WF gère les achats au sein d'une grande entreprise.Les règles d'entreprise imposent une évaluation de trois fournisseurs différents avant toute planification d'une opération d'achat.Un employé travaillant dans le service Achat sélectionne trois fournisseurs dans la liste des fournisseurs de la société.Une fois que ces fournisseurs ont été sélectionnés et informés, la société attend de recevoir leur offre.L'ordre de réception des offres n'a pas d'importance.Pour implémenter ce scénario dans WF, nous utilisons un <xref:System.Activities.Statements.ParallelForEach%601> qui permettra une recherche au sein de la liste de fournisseurs et demandera une offre de leur part.Une fois que toutes les offres ont été recueillies, la meilleure est sélectionnée et affichée.  
  
## InvokeMethod  
 L'activité <xref:System.Activities.Statements.InvokeMethod> permet l'appel de méthodes publiques dans des objets ou des types de l'étendue.Elle prend en charge l'appel de méthodes statiques et d'instances avec ou sans paramètres \(y compris les tableaux de paramètres\), ainsi que les méthodes génériques.Elle permet également l'exécution de la méthode de façon synchrone et de façon asynchrone.  
  
### Mise en route  
  
-   Dans [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], créez une application console de workflow.Ajoutez une activité <xref:System.Activities.Statements.InvokeMethod> dans le concepteur de workflow et configurez\-y des méthodes d'instances et statiques.  
  
-   Exemples :  
  
    -   [InvokeMethod](../../../docs/framework/windows-workflow-foundation/samples/invokemethod.md)  
  
-   Documentation relative au concepteur : [Concepteur d'activités InvokeMethod](../Topic/InvokeMethod%20Activity%20Designer.md)  
  
### Scénarios InvokeMethod  
  
-   Une méthode doit être appelée dans un objet de l'étendue.Par exemple, une valeur doit être ajoutée à un dictionnaire.La méthode d'ajout de l'instance du dictionnaire est appelée, puis la clé et la valeur sont fournies.  
  
-   Une méthode doit être appelée sur un objet CLR hérité.Au lieu de créer une activité personnalisée pour encapsuler l'appel dans cette classe héritée, s'il se trouve dans l'étendue pendant l'exécution du flux de travail, il est possible d'utiliser <xref:System.Activities.Statements.InvokeMethod>.  
  
## Activités de gestion des erreurs  
 L'activité <xref:System.Activities.Statements.TryCatch> fournit un mécanisme d'interception d'exceptions qui se produisent lors de l'exécution d'un ensemble d'activités contenues \(similaire à la construction Try\/Catch dans C\#\/VB\).<xref:System.Activities.Statements.TryCatch> permet la gestion des exceptions au niveau du flux de travail.Si une exception non gérée est levée, le flux de travail est abandonné et le bloc Finally n'est pas exécuté.Ce comportement est cohérent avec le langage C\#.  
  
### Mise en route  
  
-   Dans [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], créez une application console de workflowAjoutez une activité <xref:System.Activities.Statements.TryCatch> dans le concepteur de workflow.  
  
-   Exemples :  
  
    1.  [Gestion des erreurs dans une activité Flowchart à l'aide de TryCatch](../../../docs/framework/windows-workflow-foundation/samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)  
  
    2.  [Utilisation d'activités procédurales](../../../docs/framework/windows-workflow-foundation/samples/using-procedural-activities.md)  
  
-   Documentation relative au concepteur : [Concepteurs d'activités de gestion des erreurs](../Topic/Error%20Handling%20Activity%20Designers.md)  
  
### Scénarios de gestion des erreurs  
 Un ensemble d'activités doit être exécuté et une logique spécifique être exécutée en cas d'erreur.Si, au cours de la logique de gestion des erreurs, il apparaît qu'il n'est pas possible de remédier à l'erreur, l'exception est à nouveau levée et l'activité parente \(ou l'hôte\) se charge du problème.  
  
## Activité Pick  
 L'activité <xref:System.Activities.Statements.Pick> fournit une modélisation de flux de contrôle basée sur les événements dans WF.<xref:System.Activities.Statements.Pick> contient de nombreuses branches, où chacune d'entre elles attend qu'un événement particulier se produise avant de s'exécuter.Dans cette configuration, un <xref:System.Activities.Statements.Pick> se comporte de manière similaire à un <xref:System.Activities.Statements.Switch%601> dans lequel l'activité exécutera un seul des jeux d'événements qu'elle écoute.Chaque branche est pilotée par l'événement et celui qui se produit exécute la branche correspondante.Toutes les autres branches annulent et arrêtent l'écoute des événements.  
  
### Mise en route  
  
-   Dans [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], créez une application console de workflow.Ajoutez une activité <xref:System.Activities.Statements.Pick> dans le concepteur de workflow.  
  
-   Exemple : [Utilisation de l'activité Pick](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md)  
  
-   Documentation relative au concepteur : [Concepteur d'activités Pick](../Topic/Pick%20Activity%20Designer.md)  
  
### Scénario de l'activité Pick  
 Un utilisateur doit être invité à entrer des informations.Dans des circonstances normales, le développeur utiliserait un appel de méthode similaire à <xref:System.Console.ReadLine%2A> pour inviter un utilisateur à entrer des données.Le problème avec cette configuration est que le programme attend que l'utilisateur entre des données.Dans ce scénario, un délai d'attente est nécessaire pour débloquer une activité bloquante.Dans la plupart des scénarios, une tâche doit être effectuée pendant une durée déterminée.La définition d'un délai d'attente pour une activité bloquante fait partie des cas où Pick apporte une grande valeur ajoutée.  
  
## Service de routage WCF  
 Le service de routage est conçu comme un routeur logiciel générique qui vous permet de contrôler la manière dont les messages [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] circulent entre vos clients et services. Il vous permet de découpler vos clients de vos services, ce qui vous confère une liberté beaucoup plus grande en termes de configurations pouvant être prises en charge et de flexibilité dans la manière d'héberger vos services. Dans .NET 3.5, les clients et les services étaient étroitement liés ; un client devait tout savoir des services dont il avait besoin pour communiquer, ainsi que leur emplacement.Par ailleurs, WCF présentait les limitations suivantes dans .Net Framework 3.5 :  
  
-   La gestion des erreurs était complexe car cette logique devait être codée en dur côté client.  
  
-   Les clients et les services devaient toujours utiliser les mêmes liaisons.  
  
-   Les services étaient rarement conçus de manière appropriée : il est plus facile de faire communiquer le client avec un service qui implémente tout un ensemble, plutôt que de choisir entre plusieurs services.  
  
 La conception du service de routage dans .Net 4 facilite la résolution de ces problèmes.Le nouveau service de routage présente les fonctionnalités suivantes :  
  
1.  Routage basé sur le contenu \(les objets <xref:System.ServiceModel.Dispatcher.MessageFilter> examinent un message afin de déterminer sa destination.\)  
  
2.  Pontage de protocoles \(transport et message\)  
  
3.  Gestion des erreurs \(le routeur intercepte les exceptions de communication et bascule sur les points de terminaison de sauvegarde\)  
  
4.  Mise à jour dynamique \(en mémoire\) de <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> et configuration du routage.  
  
### Mise en route  
  
1.  Documentation : [Routage](../../../docs/framework/wcf/feature-details/routing.md)  
  
2.  Exemples : [Services de routage &#91;exemples WCF&#93;](../../../docs/framework/wcf/samples/routing-services.md)  
  
3.  Blog : [règles de routage](http://go.microsoft.com/fwlink/?LinkId=204956)  
  
### Scénarios de routage  
 Le service de routage s'avère utile dans les scénarios suivants :  
  
-   Les clients peuvent communiquer avec plusieurs services sans avoir à s'adresser à l'ensemble d'entre eux directement.  
  
-   Les clients peuvent apporter une logique supplémentaire à une demande du client afin de déterminer la destination du routage  
  
-   Décomposez les opérations effectuées par un client en plusieurs implémentations du service sans refactoriser le client.  
  
-   Les clients et les services peuvent présenter différentes liaisons avec différents paramètres de sécurité.  
  
-   Les clients peuvent être configurés de manière à être plus fiables en cas de défaillance ou d'indisponibilité des services.  
  
## Discovery WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Discovery est une technologie d'infrastructure qui vous permet d'incorporer un mécanisme de découverte à votre infrastructure d'applications.Vous pouvez vous en servir pour rendre votre service détectable et configurer vos clients pour qu'ils recherchent des services.Les clients n'ont plus besoin d'être codés en dur avec un point de terminaison, ce qui rend votre application plus fiable et plus tolérante aux pannes.Discovery est la plateforme parfaite pour intégrer des fonctionnalités d'auto\-configuration à votre application.  
  
 Le produit repose sur la norme WS\-Discovery.Il est conçu pour être interopérable, extensible et générique.Le produit prend en charge deux modes d'opération :  
  
1.  Managed : lorsqu'une entité sur le réseau est informée des services existants, les clients l'interrogent directement.Ce comportement est similaire à Active Directory.  
  
2.  Ad\-hoc : lorsque les clients utilisent des messages de multidiffusion pour localiser des services.  
  
 Par ailleurs, les messages de découverte ne dépendent pas du protocole réseau ; vous pouvez les utiliser avec tout protocole qui prend en charge les besoins de chaque mode.Par exemple, les messages de multidiffusion de découverte peuvent être envoyés via le canal UDP ou tout autre réseau qui prend en charge la messagerie multidiffusion. Ces points de conception, combinés à la flexibilité des fonctionnalités, vous permet d'adapter la découverte aux besoins spécifiques de votre solution.  
  
### Mise en route  
  
-   Documentation : [Découverte WCF](../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
  
-   Exemples : [Découverte \(exemples\)](../../../docs/framework/wcf/samples/discovery-samples.md)  
  
### Scénarios Discovery  
 Un développeur ne souhaite pas coder en dur les points de terminaison car la date de disponibilité de mon service n'est pas encore connue.Il souhaite plutôt choisir un service au moment du runtime.Un plus grand degré de découplage, de fiabilité et de configuration automatique est requis entre les composants de l'application.  
  
## Suivi  
 Le suivi de flux de travail donne des informations sur l'exécution d'une instance de flux de travail. Les événements de suivi sont émis à partir d'un flux de travail au niveau de l'instance de flux de travail et lors de l'exécution d'activités au sein de ce flux de travail.Un participant au suivi du flux de travail doit être ajouté à l'hôte du flux de travail pour s'abonner aux enregistrements de suivi.Les enregistrements de suivi sont filtrés à l'aide d'un profil de suivi.Le .Net Framework fournit un participant au suivi ETW \(Event Tracing for Windows\) et un profil de base est installé dans le fichier machine.config.  
  
### Mise en route  
  
1.  Dans [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], créez un projet d'application de service de flux de travail WCF.Une paire <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> sera placée dans votre zone de dessin pour le démarrage.  
  
2.  Ouvrez le fichier web.config et ajoutez un comportement de suivi ETW sans profil.  
  
    1.  Le profil par défaut est utilisé.  
  
    2.  Ouvrez l'Observateur d'événements et activez le canal analytique dans le nœud suivant : **Observateur d'événements**, **Journaux des applications et des services**, **Microsoft**, **Windows**, **Serveur d'applications\-Applications**.Cliquez avec le bouton droit sur **Analyse** et sélectionnez **Activer le journal**.  
  
    3.  Exécutez le service de flux de travail.  
  
    4.  Observez les événements de suivi du flux de travail dans l'observateur d'événements.  
  
3.  Exemples : [Suivi](../../../docs/framework/windows-workflow-foundation/samples/tracking.md)  
  
4.  Documentation conceptuelle : [Suivi et traçage de workflow](../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)  
  
## Magasin d'instances de workflow SQL  
 Le <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> est une implémentation basée sur SQL d'un magasin d'instances.Un magasin d'instances stocke l'état d'une instance en cours d'exécution avec l'ensemble des données nécessaires au chargement et à la reprise de cette instance.L'hôte du service demande au magasin d'instances d'enregistrer l'état de l'instance si le flux de travail persiste et de charger l'état de l'instance quand un message arrive pour cette instance ou qu'une activité de report arrive à expiration.  
  
### Mise en route  
  
1.  Dans [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], créez un flux de travail qui contient une activité <xref:System.Activities.Statements.Persist> implicite ou explicite.Ajoutez le comportement <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> à votre hôte de service de workflow.Cela peut se faire dans le code ou dans le fichier de configuration de l'application.  
  
2.  Exemples : [Persistance](../../../docs/framework/windows-workflow-foundation/samples/persistence.md)  
  
3.  Documentation conceptuelle : [Magasin d'instances de workflow SQL](../../../docs/framework/windows-workflow-foundation//sql-workflow-instance-store.md).