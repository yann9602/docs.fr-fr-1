---
title: "Code transparent de s&#233;curit&#233;, niveau&#160;2 | Microsoft Docs"
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
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "transparence de niveau 2"
  - "code critique de sécurité"
  - "code transparent de sécurité"
  - "transparence"
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
caps.latest.revision: 37
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 35
---
# Code transparent de s&#233;curit&#233;, niveau&#160;2
<a name="top"></a> La transparence de niveau 2 a été introduite dans le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Les trois principes de ce modèle sont le code transparent, le code critique sécurisé et le code critique de sécurité.  
  
-   Le code transparent, y compris le code qui s'exécute en mode confiance totale, peut appeler d'autre code transparent ou code critique sécurisé uniquement. Il ne peut effectuer que les actions autorisées par le jeu d'autorisations de confiance partielle du domaine \(s'il en existe un\). Voici ce que le code transparent ne peut pas faire :  
  
    -   exécuter un <xref:System.Security.CodeAccessPermission.Assert%2A> ou une élévation de privilège ;  
  
    -   contenir du code non sécurisé ou non vérifiable ;  
  
    -   appeler directement du code critique ;  
  
    -   appeler du code natif ou du code possédant l'attribut <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> ;  
  
    -   appeler un membre protégé par un <xref:System.Security.Permissions.SecurityAction> ;  
  
    -   hériter de types critiques.  
  
     Par ailleurs, les méthodes transparentes ne peuvent pas substituer des méthodes virtuelles critiques ni implémenter des méthodes d'interface critiques.  
  
-   Le code critique sécurisé est entièrement fiable, mais peut être appelé par du code transparent. Il expose une surface limitée de code de confiance totale ; des vérifications d'exactitude et de sécurité s'opèrent dans le code critique sécurisé.  
  
-   Le code critique de sécurité peut appeler n'importe quel code et bénéficie d'un niveau de confiance totale, mais il ne peut pas être appelé par du code transparent.  
  
> [!CAUTION]
>  Sécurité d'accès du code et code d'un niveau de confiance partiel  
>   
>  Le .NET Framework fournit un mécanisme, appelé « sécurité d'accès du code \(CAS\) », qui permet de mettre en œuvre différents niveaux de confiance sur différents codes exécutés dans la même application.  La sécurité d'accès du code dans .NET Framework ne doit pas être utilisée comme limite de sécurité avec du code d'un niveau de confiance partiel, notamment du code d'origine inconnue. Nous vous déconseillons de charger et d'exécuter du code d'origine inconnue sans mettre en place d'autres mesures de sécurité.  
>   
>  Cette stratégie s'applique à toutes les versions du .NET Framework, mais ne concerne pas le .NET Framework inclus dans Silverlight.  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Exemples d'utilisation et comportements](#examples)  
  
-   [Modèles de substitution](#override)  
  
-   [Règles d'héritage](#inheritance)  
  
-   [Informations et règles supplémentaires](#additional)  
  
<a name="examples"></a>   
## Exemples d'utilisation et comportements  
 Pour spécifier les règles du [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] \(transparence de niveau 2\), utilisez l'annotation suivante pour un assembly :  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level2)]  
```  
  
 Pour verrouiller les règles du .NET Framework 2.0 \(transparence de niveau 1\), utilisez l'annotation suivante :  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 Si vous n'annotez pas un assembly, les règles du [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] sont utilisées par défaut. Cependant, la meilleure pratique consiste à utiliser l'attribut <xref:System.Security.SecurityRulesAttribute> au lieu de dépendre de la valeur par défaut.  
  
### Annotation à l'échelle de l'assembly  
 Les règles suivantes s'appliquent à l'utilisation d'attributs au niveau de l'assembly :  
  
-   Aucun attribut : si vous ne spécifiez aucun attribut, le runtime considère l'ensemble du code comme du code critique de sécurité, sauf si le fait d'être critique de sécurité va à l'encontre d'une règle d'héritage \(par exemple, en cas de substitution ou d'implémentation d'une méthode d'interface ou virtuelle transparente\). Dans ces cas de figure, les méthodes sont critiques sécurisées. Si vous ne spécifiez aucun attribut, le common language runtime détermine les règles de transparence à votre place.  
  
-   `SecurityTransparent` : tout le code est transparent ; l'assembly dans son ensemble ne fait rien de privilégié ou de non sécurisé.  
  
-   `SecurityCritical` : tout le code introduit par des types dans cet assembly est critique ; le reste du code est transparent. Ce scénario équivaut à ne spécifier aucun attribut ; cependant, le common language runtime ne détermine pas automatiquement les règles de transparence. Par exemple, si vous substituez une méthode virtuelle ou abstraite ou que vous implémentez une méthode d'interface, par défaut, cette méthode est transparente. Vous devez annoter explicitement la méthode comme étant `SecurityCritical` ou `SecuritySafeCritical` ; sinon, une exception <xref:System.TypeLoadException> est levée au moment du chargement. Cette règle vaut aussi quand la classe de base et la classe dérivée se trouvent dans le même assembly.  
  
-   `AllowPartiallyTrustedCallers` \(niveau 2 uniquement\) : tout le code est transparent par défaut. Cependant, chaque type et membre individuel peut avoir d'autres attributs.  
  
 Le tableau suivant établit une comparaison entre le comportement de niveau assembly pour les niveaux 2 et 1.  
  
|Assembly \(attribut\)|Niveau 2|Niveau 1|  
|---------------------------|--------------|--------------|  
|Aucun attribut sur un assembly de niveau de confiance partielle|Les types et les membres sont transparents par défaut, mais peuvent être critiques de sécurité ou critiques sécurisés.|Tous les types et membres sont transparents.|  
|Aucun attribut|Si vous ne spécifiez aucun attribut, le common language runtime détermine les règles de transparence à votre place. Tous les types et membres sont critiques de sécurité, sauf si le fait d'être critique de sécurité va à l'encontre d'une règle d'héritage.|Sur un assembly d'un niveau de confiance totale \(dans le Global Assembly Cache ou s'il est identifié comme étant entièrement fiable dans le `AppDomain`\) tous les types sont transparents et tous les membres sont critiques sécurisés.|  
|`SecurityTransparent`|Tous les types et membres sont transparents.|Tous les types et membres sont transparents.|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|Non applicable.|Tous les types et membres sont critiques de sécurité.|  
|`SecurityCritical`|Tout le code introduit par des types dans cet assembly est critique ; le reste du code est transparent. Si vous substituez une méthode virtuelle ou abstraite ou que vous implémentez une méthode d'interface, vous devez annoter explicitement la méthode comme étant `SecurityCritical` ou `SecuritySafeCritical`.|Tout le code est transparent par défaut. Cependant, chaque type et membre individuel peut avoir d'autres attributs.|  
  
### Annotation de type et de membre  
 Les attributs de sécurité qui s'appliquent à un type s'appliquent aussi aux membres introduits par ce type. En revanche, ils ne s'appliquent pas aux substitutions virtuelles ou abstraites des implémentations de classe ou d'interface de base. L'utilisation d'attributs au niveau du type et du membre obéit aux règles suivantes :  
  
-   `SecurityCritical` : le type ou le membre est critique et peut être appelé uniquement par du code de niveau de confiance totale. Les méthodes introduites dans un type critique de sécurité sont critiques.  
  
    > [!IMPORTANT]
    >  Les méthodes virtuelles et abstraites introduites dans des classes ou interfaces de base et substituées ou implémentées dans une classe critique de sécurité sont transparentes par défaut. Elles doivent être identifiées comme étant `SecuritySafeCritical` ou `SecurityCritical`.  
  
-   `SecuritySafeCritical` : le type ou le membre est critique sécurisé. Cependant, le type ou le membre peut être appelé à partir d'un code transparent \(de niveau de confiance partielle\) et a les mêmes capacités que n'importe quel autre code critique. La sécurité du code doit faire l'objet d'un audit.  
  
 [Retour au début](#top)  
  
<a name="override"></a>   
## Modèles de substitution  
 Le tableau suivant présente les substitutions de méthodes autorisées pour la transparence de niveau 2.  
  
|Membre d'interface\/virtuel de base|Substitution\/interface|  
|-----------------------------------------|-----------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 [Retour au début](#top)  
  
<a name="inheritance"></a>   
## Règles d'héritage  
 Dans cette section, l'ordre suivant est attribué au code `Transparent`, `Critical` et `SafeCritical` en fonction de l'accès et des fonctionnalités :  
  
 `Transparent` \< `SafeCritical` \< `Critical`  
  
-   Règles pour les types : allant de gauche à droite, l'accès devient plus restrictif. Les types dérivés doivent être au moins aussi restrictifs que le type de base.  
  
-   Règles pour les méthodes : les méthodes dérivées ne peuvent pas modifier l'accessibilité à partir de la méthode de base. Pour le comportement par défaut, toutes les méthodes dérivées qui ne sont pas annotées sont `Transparent`. Les dérivés des types critiques provoquent une exception si la méthode substituée n'est pas explicitement annotée comme étant `SecurityCritical`.  
  
 Le tableau suivant présente les modèles d'héritage de type autorisés.  
  
|Classe de base|La classe dérivée peut être|  
|--------------------|---------------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`SafeCritical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Critical`|  
  
 Le tableau suivant présente les modèles d'héritage de type non autorisés.  
  
|Classe de base|La classe dérivée ne peut pas être|  
|--------------------|----------------------------------------|  
|`SafeCritical`|`Transparent`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
 Le tableau suivant présente les modèles d'héritage de méthode autorisés.  
  
|Méthode de base|La méthode dérivée peut être|  
|---------------------|----------------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 Le tableau suivant présente les modèles d'héritage de méthode non autorisés.  
  
|Méthode de base|La méthode dérivée ne peut pas être|  
|---------------------|-----------------------------------------|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
> [!NOTE]
>  Ces règles d'héritage s'appliquent aux types et membres de niveau 2. Les types contenus dans les assemblys de niveau 1 peuvent hériter des types et membres critiques de sécurité de niveau 2. Par conséquent, les types et membres de niveau 2 doivent avoir des demandes d'héritage distinctes pour les héritiers de niveau 1.  
  
 [Retour au début](#top)  
  
<a name="additional"></a>   
## Informations et règles supplémentaires  
  
### Prise en charge de LinkDemand  
 Le modèle de transparence de niveau 2 remplace le <xref:System.Security.Permissions.SecurityAction> par l'attribut <xref:System.Security.SecurityCriticalAttribute>. Dans le code hérité \(de niveau 1\), un <xref:System.Security.Permissions.SecurityAction> est automatiquement traité comme un <xref:System.Security.Permissions.SecurityAction>.  
  
### Réflexion  
 L'appel d'une méthode critique ou la lecture d'un champ critique déclenche une demande de confiance totale \(comme si vous appeliez une méthode ou un champ privé\). Autrement dit, du code de niveau de confiance totale peut appeler une méthode critique, alors que du code de niveau de confiance partielle ne le peut pas.  
  
 Les propriétés suivantes ont été ajoutées à l'espace de noms <xref:System.Reflection> pour déterminer si le type, la méthode ou le champ est `SecurityCritical`, `SecuritySafeCritical` ou `SecurityTransparent` : <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> et <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>. Ces propriétés permettent de déterminer la transparence par la réflexion plutôt que par la vérification de la présence de l'attribut. Compte tenu de la complexité des règles de transparence, vérifier la présence de l'attribut peut ne pas suffire.  
  
> [!NOTE]
>  Une méthode `SafeCritical` retourne la valeur `true` pour <xref:System.Type.IsSecurityCritical%2A>``et <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, car `SafeCritical` est réellement critique \(ses fonctionnalités sont les mêmes que celles du code critique, mais il peut être appelé à partir d'un code transparent\).  
  
 Les méthodes dynamiques héritent de la transparence des modules auxquels elles sont attachées ; elles n'héritent pas de la transparence du type \(si elles sont attachées à un type\).  
  
### Ignorer la vérification en mode confiance totale  
 Vous pouvez ignorer la vérification pour les assemblys transparents de niveau de confiance totale en attribuant à la propriété <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> la valeur `true` dans l'attribut <xref:System.Security.SecurityRulesAttribute> :  
  
 `[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`  
  
 La valeur par défaut de la propriété <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> étant `false`, elle doit avoir la valeur `true` pour ignorer la vérification. Cela doit être fait uniquement à des fins d'optimisation. Vous devez vous assurer que le code transparent contenu dans l'assembly peut être vérifié à l'aide de l'option `transparent` de l'[outil PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md).  
  
## Voir aussi  
 [Code transparent de sécurité, niveau 1](../../../docs/framework/misc/security-transparent-code-level-1.md)   
 [Modifications de sécurité](../../../docs/framework/security/security-changes.md)