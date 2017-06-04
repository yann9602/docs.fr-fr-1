---
title: "XAML Security Considerations | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security [XAML Services], .NET XAML services"
  - "XAML security [XAML Services]"
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
caps.latest.revision: 7
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 7
---
# XAML Security Considerations
Cette rubrique décrit les meilleures pratiques relatives à la sécurité des applications lors de l'utilisation du langage XAML et de l'API des services XAML .NET Framework.  
  
## XAML non fiable dans les applications  
 En général, le langage XAML non fiable correspond aux sources XAML que votre application n'inclut pas ou n'émet pas spécifiquement.  
  
 Le XAML compilé ou stocké en tant que ressource de type `resx` dans un assembly approuvé et signé n'est pas fondamentalement non fiable.  Vous pouvez approuver le langage XAML de la même manière que vous approuvez l'assembly dans son ensemble.  Dans la plupart des cas, vous aurez uniquement à vous préoccuper des aspects d'approbation du XAML libre \(source XAML que vous chargez à partir d'un flux ou d'une autre E\/S\).  Le XAML libre ne constitue pas un composant ou une fonctionnalité spécifique d'un modèle d'application avec infrastructure de déploiement et d'empaquetage.  Toutefois, un assembly peut implémenter un comportement impliquant le chargement de XAML libre.  
  
 En ce qui concerne le langage XAML non fiable, vous devez le traiter de la même manière que le code non fiable.  Utilisez le sandboxing ou d'autres métaphores pour empêcher le langage XAML non fiable d'accéder à votre code de confiance.  
  
 La nature des fonctions XAML permet au langage XAML de créer des objets et de définir leurs propriétés.  Ces fonctions incluent également l'accès aux convertisseurs de types, le mappage et l'accès aux assemblys dans le domaine d'application, l'utilisation d'extensions de balisage, de blocs `x:Code`, etc.  
  
 Outre ses fonctions relatives au langage, XAML est utilisé pour la définition de l'interface utilisateur dans de nombreuses technologies.  Le chargement de langage XAML non fiable peut signifier le chargement d'une interface utilisateur malveillante \(usurpation\).  
  
## Partage du contexte entre les lecteurs et les writers  
 En général, l'architecture des services XAML .NET Framework pour les lecteurs et writers XAML requiert le partage entre un lecteur XAML et un writer XAML, ou un contexte de schéma XAML partagé.  Un partage d'objets ou de contextes peut être requis si vous écrivez une logique de boucle pour le nœud XAML ou si vous proposez un chemin d'enregistrement personnalisé.  Vous ne devez pas partager les instances des lecteurs XAML, un contexte de schéma XAML autre que celui par défaut ou les paramètres des classes des lecteurs\/writers XAML entre le code approuvé et le code non fiable.  
  
 La plupart des scénarios et des opérations impliquant l'écriture d'objets XAML pour l'enregistrement d'un type basé sur CLR peuvent uniquement utiliser le contexte de schéma XAML par défaut.  Le contexte de schéma XAML par défaut n'inclut pas explicitement les paramètres qui pourraient compromettre la confiance totale.  Par conséquent, il est plus sûr de partager le contexte entre des composants de lecteurs\/writers XAML approuvés et non fiables.  Toutefois, dans ce cas, il est préférable de conserver ces lecteurs et ces writers dans des portées <xref:System.AppDomain> distinctes, dont l'une est spécifiquement conçue\/mise en bac à sable pour la confiance partielle.  
  
## Espaces de noms XAML et niveau de confiance des assemblys  
 La syntaxe et la définition non qualifiées de base qui régissent la manière dont le langage XAML interprète un mappage d'espace de noms XAML personnalisé à un assembly ne font pas la distinction entre un assembly approuvé et un assembly non fiable chargés dans le domaine d'application.  Par conséquent, il est techniquement possible pour un assembly non fiable d'usurper le mappage d'espace de noms XAML prévu d'un assembly approuvé et de capturer l'objet déclaré et les informations de propriété d'une source XAML.  Si vous avez défini des spécifications de sécurité pour éviter cette situation, le mappage d'espace de noms XAML souhaité doit être établi à l'aide de l'une des techniques suivantes :  
  
-   Utilisez un nom d'assembly qualifié complet avec un nom fort pour tous les mappages d'espace de noms XAML établis par le code XAML de votre application.  
  
-   Restreignez le mappage de l'assembly à un jeu fixe d'assemblys de référence en créant une classe <xref:System.Xaml.XamlSchemaContext> spécifique pour vos lecteurs et writers d'objets XAML.  Consultez <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>.  
  
## Mappage de type XAML et accès au système de type  
 Le langage XAML prend en charge son propre système de type, qui ressemble énormément à la manière dont CLR implémente le système de type CLR de base.  Toutefois, pour certains aspects de la prise en compte des types dans lesquels vous prenez des décisions d'approbation sur un type en fonction de ses informations de type, vous devez vous référer aux informations sur les types dans les types de stockage CLR.  Cela est dû au fait que certaines fonctions de signalement spécifiques du système de type XAML sont restées ouvertes en tant que méthodes virtuelles et qu'elles ne sont donc pas intégralement contrôlées par les implémentations des services XAML .NET Framework d'origine.  Ces points d'extensibilité existent car le système de type XAML est extensible, pour correspondre à l'extensibilité du langage XAML lui\-même et de ses éventuelles stratégies de mappage de type et à l'implémentation CLR par défaut et au contexte de schéma XAML par défaut.  Pour plus d'informations, consultez les notes spécifiques relatives aux différentes propriétés de <xref:System.Xaml.XamlType> et de <xref:System.Xaml.XamlMember>.  
  
## Voir aussi  
 <xref:System.Xaml.Permissions.XamlAccessLevel>