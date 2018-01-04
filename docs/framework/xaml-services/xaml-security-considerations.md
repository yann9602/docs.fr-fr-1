---
title: "Considérations sur la sécurité XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b58719f36cd911497c5cd892610330688221e7ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-security-considerations"></a>Considérations sur la sécurité XAML
Cette rubrique décrit les meilleures pratiques pour la sécurité dans les applications lorsque vous utilisez XAML et l’API des Services XAML .NET Framework.  
  
## <a name="untrusted-xaml-in-applications"></a>XAML non fiable dans les Applications  
 Dans le sens de la plus général, XAML non fiable est n’importe quelle source XAML que votre application ne pas spécifiquement inclure ou émettre des.  
  
 XAML compilé ou stocké en tant qu’un `resx`-ressource de type dans un assembly approuvé et signé n’est pas fondamentalement non fiable. Vous pouvez approuver le code XAML que vous faites confiance à l’assembly dans son ensemble. Dans la plupart des cas, vous ne sont concernés par les aspects d’approbation du XAML libre, qui est une source XAML que vous chargez à partir d’un flux de données ou autres e/s. XAML libre n’est pas un composant spécifique ou une fonctionnalité d’un modèle d’application avec une infrastructure de l’empaquetage et le déploiement. Toutefois, un assembly peut implémenter un comportement impliquant le chargement de XAML libre.  
  
 Pour XAML non approuvé, vous devez le traiter généralement le même comme s’il s’agissait de code non fiable. Utilisez le sandboxing ou autres métaphores pour empêcher des XAML non fiable d’accéder à votre code de confiance.  
  
 La nature des fonctions XAML permet le code XAML pour construire des objets et définir leurs propriétés. Ces fonctions incluent également l’accès aux convertisseurs de type, le mappage et l’accès aux assemblys dans le domaine d’application, à l’aide des extensions de balisage, `x:Code` blocs et ainsi de suite.  
  
 Outre ses fonctionnalités au niveau du langage, XAML est utilisé pour la définition de l’interface utilisateur dans de nombreuses technologies. Chargement de XAML non fiable peut signifier que le chargement d’une interface d’utilisateur d’usurpation de contenu malveillant.  
  
## <a name="sharing-context-between-readers-and-writers"></a>Partage du contexte entre les lecteurs et Writers  
 L’architecture de Services XAML .NET Framework pour les lecteurs et writers XAML requiert souvent le partage d’un lecteur XAML et un writer XAML, ou un contexte de schéma XAML partagé. Partage d’objets ou contextes peut être nécessaire si vous écrivez la logique de boucle de nœud XAML, ou en fournissant une personnalisée de chemin d’enregistrement. Ne partagez pas les instances de lecteur XAML, le contexte de schéma XAML par défaut ou les paramètres pour les classes de lecteur/writer XAML entre le code et non approuvé.  
  
 La plupart des scénarios et des opérations impliquant l’écriture d’un stockage basé sur CLR de type d’objet XAML peuvent simplement utiliser de contexte de schéma XAML par défaut. Le contexte de schéma XAML par défaut n’inclut pas explicitement les paramètres qui pourraient compromettre la confiance totale. Il est donc possible de partager le contexte entre les composants de lecteur/writer XAML approuvés et non approuvés. Toutefois, si vous faites cela, il est toujours recommandé de conserver ces lecteurs et writers dans distinct <xref:System.AppDomain> étendues, avec un d’eux spécifiquement prévu/bac à sable pour la confiance partielle.  
  
## <a name="xaml-namespaces-and-assembly-trust"></a>Espaces de noms XAML et l’approbation de l’Assembly  
 La syntaxe non qualifié de base et la définition de la façon dont XAML interprète un mappage d’espace de noms XAML personnalisé à un assembly ne fait pas la distinction entre un assembly approuvé et non approuvés chargés dans le domaine d’application. Par conséquent, il est techniquement possible pour un assembly non fiable d’usurper le mappage d’espace de noms XAML prévu d’un assembly de confiance et de capturer les objet déclaré d’une source XAML et les informations sur les propriétés. Si vous avez des exigences de sécurité pour éviter cette situation, votre mappage d’espace de noms XAML souhaité doit être créée à l’aide d’une des techniques suivantes :  
  
-   Utilisez un nom complet d’assembly avec nom fort dans tout mappage d’espace de noms XAML par le code XAML de votre application.  
  
-   Limiter le mappage à un ensemble fixe d’assemblys de référence, en créant un spécifique de l’assembly <xref:System.Xaml.XamlSchemaContext> pour vos lecteurs XAML et les writers d’objet. Consultez <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>.  
  
## <a name="xaml-type-mapping-and-type-system-access"></a>Mappage de Type XAML et l’accès au système de Type  
 XAML prend en charge son propre système de type, qui est un homologue de la manière dont le CLR implémente le système de type CLR base de nombreuses manières. Toutefois, pour certains aspects de la reconnaissance de type dans lesquels vous prenez des décisions d’approbation sur un type en fonction de ses informations de type, vous devez vous référer aux informations de type dans le CLR, types de stockage. Il s’agit, puisque les fonctions de rapport spécifiques du système de type XAML sont laissés ouverts en tant que méthodes virtuelles et ne sont donc pas entièrement sous le contrôle des implémentations de Services XAML .NET Framework d’origine. Ces points d’extensibilité existent car le système de type XAML est extensible, pour correspondre à l’extensibilité du langage XAML lui-même et ses stratégies de mappage de type alternatives possible par rapport à l’implémentation de CLR par défaut et le contexte de schéma XAML par défaut. Pour plus d’informations, consultez les notes spécifiques sur les différentes propriétés de <xref:System.Xaml.XamlType> et <xref:System.Xaml.XamlMember>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xaml.Permissions.XamlAccessLevel>
