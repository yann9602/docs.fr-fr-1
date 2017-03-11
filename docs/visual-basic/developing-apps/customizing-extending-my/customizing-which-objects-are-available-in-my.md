---
title: "Customizing Which Objects are Available in My (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My namespace, customizing"
  - "My namespace"
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Customizing Which Objects are Available in My (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Cette rubrique décrit comment vous pouvez contrôler les objets `My` qui sont activés en définissant la constante de compilation conditionnelle `_MYTYPE` de votre projet.  L'environnement de développement intégré \(IDE, Integrated Development Environment\) de [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] conserve la constante de compilation conditionnelle `_MYTYPE` pour un projet synchronisé avec le type du projet.  
  
## Valeurs \_MYTYPE prédéfinies  
 Vous devez utiliser l'option du compilateur `/define` pour définir la constante de compilation conditionnelle `_MYTYPE`.  Lorsque vous spécifiez votre propre valeur pour la constante `_MYTYPE`, vous devez entourer la valeur de chaîne de barres obliques inverses\/guillemets \(\\"\).  Par exemple, vous pouvez utiliser :  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Ce tableau affiche la constante de compilation conditionnelle `_MYTYPE` affectée à plusieurs types de projet.  
  
|Type de projet|Valeur \_MYTYPE|  
|--------------------|---------------------|  
|Bibliothèque de classes|"Windows"|  
|Application console|"Console"|  
|Web|"Web"|  
|Bibliothèque de contrôles Web|"WebControl"|  
|Application Windows|"WindowsForms"|  
|Application Windows, lorsque vous démarrez avec un `Sub Main` personnalisé|"WindowsFormsWithCustomSubMain"|  
|Bibliothèque de contrôles Windows|"Windows"|  
|Service Windows|"Console"|  
|Vide|"Empty"|  
  
> [!NOTE]
>  Toutes les comparaisons de chaînes de la compilation conditionnelle respectent les majuscules et les minuscules, quelle que soit la manière dont l'instruction `Option Compare` est définie.  
  
## Constantes de compilation \_MY dépendantes  
 La constante de compilation conditionnelle `_MYTYPE` contrôle à son tour les valeurs de plusieurs autres constantes de compilation `_MY` :  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|"Console"|"Console"|"Windows"|Indéfini|"Windows"|TRUE|  
|"Custom"|Indéfini|Indéfini|Indéfini|Indéfini|Indéfini|  
|"Empty"|Indéfini|Indéfini|Indéfini|Indéfini|Indéfini|  
|"Web"|Indéfini|"Web"|FALSE|"Web"|FALSE|  
|"WebControl"|Indéfini|"Web"|FALSE|"Web"|TRUE|  
|"Windows" ou ""|"Windows"|"Windows"|Indéfini|"Windows"|TRUE|  
|"WindowsForms"|"WindowsForms"|"Windows"|TRUE|"Windows"|TRUE|  
|"WindowsFormsWithCustomSubMain"|"Console"|"Windows"|TRUE|"Windows"|TRUE|  
  
 Par défaut, les constantes de compilation conditionnelle non définies ont la valeur `FALSE`.  Vous pouvez spécifier des valeurs pour les constantes non définies lors de la compilation de votre projet pour substituer le comportement par défaut.  
  
> [!NOTE]
>  Lorsque `_MYTYPE` a la valeur "Custom", le projet contient l'espace de noms `My` mais ne contient pas d'objets.  Toutefois, si vous affectez la valeur "Vide" à `_MYTYPE`, le compilateur ne pourra pas ajouter l'espace de noms `My` et ses objets.  
  
 Ce tableau décrit les effets des valeurs prédéfinies des constantes de compilation `_MY`.  
  
|Constante|Signification|  
|---------------|-------------------|  
|`_MYAPPLICATIONTYPE`|Active `My.Application`, si la constante est "Console", Windows" ou "WindowsForms" :<br /><br /> -   La version "Console" dérive de <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> et comporte moins de membres que la version "Windows".<br />-   La version "Windows" dérive de <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> et a moins de membres que la version "WindowsForms".<br />-   La version "WindowsForms" de `My.Application` dérive de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>.  Si la constante `TARGET` est définie pour être "winexe", la classe inclut une méthode `Sub Main`.|  
|`_MYCOMPUTERTYPE`|Active `My.Computer`, si la constante est "Web" ou "Windows" :<br /><br /> -   La version "Web" dérive de <xref:Microsoft.VisualBasic.Devices.ServerComputer> et a moins de membres que la version "Windows".<br />-   La version "Windows" de `My.Computer` dérive de <xref:Microsoft.VisualBasic.Devices.Computer>.|  
|`_MYFORMS`|Active `My.Forms`, si la constante est `TRUE`.|  
|`_MYUSERTYPE`|Active `My.User`, si la constante est "Web" ou "Windows" :<br /><br /> -   La version "Web" de `My.User` est associée à l'identité de l'utilisateur de la demande HTTP actuelle.<br />-   La version "Windows" de `My.User` est associée à l'entité de sécurité du thread actuel.|  
|`_MYWEBSERVICES`|Active `My.WebServices`, si la constante est `TRUE`.|  
|`_MYTYPE`|Active `My.Log`, `My.Request` et `My.Response`, si la constante est "Web".|  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.Logging.Log>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [How My Depends on Project Type](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [\/define](../../../visual-basic/reference/command-line-compiler/define.md)   
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.Request Object](../../../visual-basic/language-reference/objects/my-request-object.md)   
 [My.Response Object](../../../visual-basic/language-reference/objects/my-response-object.md)   
 [My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)