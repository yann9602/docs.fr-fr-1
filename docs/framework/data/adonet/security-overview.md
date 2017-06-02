---
title: "Vue d&#39;ensemble de la s&#233;curit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Vue d&#39;ensemble de la s&#233;curit&#233;
La sécurisation d'une application est un processus permanent.  Un développeur ne peut à aucun moment garantir qu'une application est à l'abri de toute attaque car il est impossible de prédire les types d'attaques futures que les nouvelles technologies permettront de faire apparaître.  Inversement, le fait que personne n'a encore découvert \(ou révélé\) les défaillances de la sécurité d'un système ne signifie pas qu'il n'en existe pas ou qu'il ne peut pas en exister.  Vous devez planifier la sécurité au cours de la phase de conception du projet, ainsi que la manière dont la sécurité sera maintenue tout au long de la durée de vie de l'application.  
  
## Concevoir la sécurité  
 L'un des principaux problèmes liés au développement d'applications sécurisées est que la sécurité constitue souvent un aspect pris en considération après coup, après qu'un projet a été complètement codé.  Le fait de ne pas concevoir la sécurité dans une application au début engendre des applications non sécurisées, car ce qui rend une application sûre n'a pas été pris en compte.  
  
 Lorsque la sécurité est implémentée en dernière minute, cela entraîne également davantage de bogues, tels que des blocages de logiciels suite aux nouvelles restrictions ou la nécessité de réécrire du code pour la prise en charge de fonctionnalités non prévues initialement.  Chaque ligne de code révisé ouvre la possibilité d'introduire un nouveau bogue.  C'est pourquoi vous devez songer à la sécurité à un stade précoce du processus de développement, de façon à pouvoir la développer en même temps que les nouvelles fonctionnalités.  
  
### Modélisation des menaces  
 Vous ne pouvez pas protéger un système contre une attaque si vous ne comprenez pas toutes les attaques potentielles auxquelles il est exposé.  Le processus d'évaluation des menaces de sécurité, appelé *modélisation des menaces*, est nécessaire pour déterminer la probabilité et les ramifications des brèches de sécurité dans votre application ADO.NET.  
  
 La modélisation des menaces est constituée de trois étapes principales : compréhension de la perspective de l'adversaire, caractérisation de la sécurité du système et détermination des menaces.  
  
 La modélisation des menaces représente une approche itérative pour évaluer les vulnérabilités de votre application, afin de déceler les plus dangereuses, qui exposent les données les plus sensibles.  Une fois ces vulnérabilités identifiées, vous les classez par ordre de gravité et créez un ensemble de contre\-mesures pour contrer les menaces selon leurs niveaux de priorité respectifs.  
  
 Pour plus d'informations, voir les ressources ci\-dessous.  
  
|Ressource|Description|  
|---------------|-----------------|  
|Le site [Modélisation des menaces](http://go.microsoft.com/fwlink/?LinkId=98353) sur le Centre de développment de la sécurité MSDN|Les ressources de cette page vous aideront à comprendre le processus de modélisation des menaces et à construire des modèles de menaces que vous pouvez utiliser pour sécuriser vos propres applications|  
  
## Principe des privilèges minimum  
 Lorsque vous concevez, générez et déployez votre application, vous devez partir du principe qu'elle va être attaquée.  Souvent, ces attaques proviennent de code malveillant qui s'exécute avec les autorisations de l'utilisateur exécutant le code.  D'autres peuvent provenir de code bien intentionné qui a été exploité par un pirate.  Lorsque vous planifiez la sécurité, supposez toujours que le pire scénario va se produire.  
  
 Vous pouvez employer une contre\-mesure qui consiste à tenter d'ériger autant de murs autour de votre code que possible, en l'exécutant avec des privilèges minimum.  Le principe des privilèges minimum consiste à accorder des droits sur un minimum de code pendant la durée de temps la plus courte nécessaire pour effectuer le travail.  
  
 La recommandation concernant la création d'applications sécurisées consiste à démarrer sans autorisation du tout, puis d'ajouter les autorisations les plus minimales pour la tâche spécifique en cours de réalisation.  En revanche, démarrer avec toutes les autorisations puis en refuser individuellement génère des applications non sécurisées, plus difficiles à tester et à maintenir en raison de l'existence éventuelle de brèches dans la sécurité causées par l'octroi involontaire d'autorisations superflues.  
  
 Pour plus d'informations sur la sécurisation de vos applications, voir les ressources suivantes.  
  
|Ressource|Description|  
|---------------|-----------------|  
|[Sécurisation des applications](../Topic/Securing%20Applications.md)|Contient des liens vers des rubriques de sécurité générales.  Contient également des liens vers des rubriques pour sécuriser des applications distribuées, des applications Web, des applications mobiles et des applications de bureau.|  
  
## sécurité d'accès du code \(CAS, Code Access Security\)  
 La sécurité d'accès au code est un mécanisme qui aide à limiter l'accès dont dispose le code aux ressources et opérations protégées.  Dans le .NET Framework, la sécurité d'accès du code remplit les fonctions suivantes :  
  
-   Définit les autorisations et les jeux d'autorisations qui représentent le droit d'accéder à diverses ressources système.  
  
-   Permet aux administrateurs de configurer la stratégie de sécurité en associant les ensembles d'autorisations à des groupes de code.  
  
-   Autorise le code à demander les autorisations nécessaires à son exécution, ainsi que les autorisations éventuellement utiles, puis spécifie les autorisations que le code ne doit jamais avoir.  
  
-   Octroie des autorisations à chaque assembly chargé, en fonction des autorisations demandées par le code et des opérations autorisées par la stratégie de sécurité.  
  
-   Permet au code de demander que ses appelants possèdent des autorisations spécifiques.  
  
-   Permet au code de demander que ses appelants possèdent une signature numérique, ce qui permet ainsi que l'appel du code protégé soit uniquement effectué par des appelants d'une organisation ou d'un site spécifique.  
  
-   Applique des restrictions sur le code au moment de l'exécution en comparant les autorisations accordées de chaque appelant sur la pile d'appels avec les autorisations que les appelants doivent posséder.  
  
 Pour réduire l'étendue des dommages pouvant se produire en cas d'attaque réussie, choisissez un contexte de sécurité pour votre code, qui accorde un accès uniquement aux ressources dont il a besoin pour effectuer son travail et à aucune autre.  
  
 Pour plus d'informations, voir les ressources ci\-dessous.  
  
|Ressource|Description|  
|---------------|-----------------|  
|[Sécurité d'accès du code et ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)|Décrit les interactions entre la sécurité d'accès du code, la sécurité basée sur les rôles et les environnements avec un niveau de confiance partielle depuis la perspective d'une application ADO.NET.|  
|[Code Access Security](http://msdn.microsoft.com/fr-fr/23a20143-241d-4fe5-9d9f-3933fd594c03)|Contient des liens vers des rubriques supplémentaires qui décrivent la sécurité d'accès du code dans le .NET Framework.|  
  
## Sécurité de base de données  
 Le principe des privilèges minimum s'applique également à votre source de données.  Ci\-dessous figurent quelques\-unes des instructions générales concernant la sécurité de la base de données :  
  
-   Créez des comptes avec les privilèges les moins élevés possible.  
  
-   N'autorisez pas les utilisateurs à accéder aux comptes d'administration uniquement pour faire fonctionner le code.  
  
-   Ne retournez pas de messages d'erreur côté serveur pour les applications clientes.  
  
-   Validez toutes les entrées sur le client et le serveur.  
  
-   Utilisez des commandes paramétrées et évitez les instructions SQL dynamiques.  
  
-   Activez l'audit de sécurité et la journalisation pour la base de données que vous utilisez, afin d'être alerté en cas de brèches de sécurité.  
  
 Pour plus d'informations, voir les ressources ci\-dessous.  
  
|Ressource|Description|  
|---------------|-----------------|  
|[Sécurité de SQL Server](../../../../docs/framework/data/adonet/sql/sql-server-security.md)|Fournit une vue d'ensemble de la sécurité de SQL Server avec des scénarios d'application qui fournissent des conseils pour créer des applications ADO.NET sécurisées qui ciblent SQL Server.|  
|[Recommendations for Data Access Strategies](http://msdn.microsoft.com/fr-fr/72411f32-d12a-4de8-b961-e54fca7faaf5)|Fournit des recommandations pour l'accès aux données et l'exécution d'opérations de base de données.|  
  
## Stratégie et administration de sécurité  
 Une administration incorrecte de la sécurité d'accès du code peut potentiellement créer des failles en matière de sécurité.  Une fois qu'une application a été déployée, des techniques de surveillance de la sécurité doivent être utilisées et les risques évalués à mesure que de nouvelles menaces émergent.  
  
 Pour plus d'informations, voir les ressources ci\-dessous.  
  
|Ressource|Description|  
|---------------|-----------------|  
|[NIB: Security Policy Management](http://msdn.microsoft.com/fr-fr/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9)|Fournit des informations sur la création et l'administration de la stratégie de sécurité.|  
|[NIB: Security Policy Best Practices](http://msdn.microsoft.com/fr-fr/d49bc4d5-efb7-4caa-a2fe-e4d3cec63c05)|Fournit des liens qui décrivent comment administrer la stratégie de sécurité.|  
  
## Voir aussi  
 [Sécurisation des applications ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)   
 [PAVE Security in Native and .NET Framework Code](http://msdn.microsoft.com/fr-fr/bd61be84-c143-409a-a75a-44253724f784)   
 [Sécurité de SQL Server](../../../../docs/framework/data/adonet/sql/sql-server-security.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)