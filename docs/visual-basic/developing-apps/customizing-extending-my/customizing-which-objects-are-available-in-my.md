---
title: Personnalisation des objets sont disponibles dans My (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My namespace, customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6791398270e4348adf356eb36a385bfbefde873c
ms.lasthandoff: 03/13/2017

---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Personnalisation de la disponibilité ou non des objets dans My (Visual Basic)
Cette rubrique décrit comment vous pouvez contrôler quels `My` objets sont activés par la configuration de votre projet `_MYTYPE` constante de compilation conditionnelle. Le [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] un environnement de développement intégré (IDE) conserve les `_MYTYPE` constante de compilation conditionnelle pour un projet synchronisé avec le type du projet.  
  
## <a name="predefined-mytype-values"></a>Valeurs _MYTYPE prédéfinies  
 Vous devez utiliser le `/define` option du compilateur pour définir le `_MYTYPE` constante de compilation conditionnelle. Lorsque vous spécifiez votre propre valeur pour la `_MYTYPE` constante, vous devez placer la valeur de chaîne dans la barre oblique inverse/guillemets (\\») séquences. Par exemple, vous pouvez utiliser :  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Ce tableau affiche le `_MYTYPE` constante de compilation conditionnelle a la valeur pour plusieurs types de projet.  
  
|Type de projet|Valeur _MYTYPE|  
|------------------|--------------------|  
|Bibliothèque de classes|« Windows »|  
|Application console|« Console »|  
|Web|« Web »|  
|Bibliothèque de contrôles web|« WebControl »|  
|Application Windows|« WindowsForms »|  
|Application Windows, lorsque vous démarrez avec personnalisé`Sub Main`|« WindowsFormsWithCustomSubMain »|  
|Bibliothèque de contrôles Windows|« Windows »|  
|Service Windows|« Console »|  
|Empty|« Vide »|  
  
> [!NOTE]
>  Toutes les comparaisons de chaînes de la compilation conditionnelle respectent la casse, quel que soit la façon dont la `Option Compare` instruction est défini.  
  
## <a name="dependent-my-compilation-constants"></a>Constantes de Compilation _MY dépendantes  
 Le `_MYTYPE` constante de compilation conditionnelle, contrôle à son tour, les valeurs de plusieurs autres `_MY` constantes de compilation :  
  
|_MYTYPE|_MYAPPLICATIONTYPE|_MYCOMPUTERTYPE|_MYFORMS|_MYUSERTYPE|_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|« Console »|« Console »|« Windows »|non définie|« Windows »|TRUE|  
|« Custom »|non définie|non définie|non définie|non définie|non définie|  
|« Vide »|non définie|non définie|non définie|non définie|non définie|  
|« Web »|non définie|« Web »|FALSE|« Web »|FALSE|  
|« WebControl »|non définie|« Web »|FALSE|« Web »|TRUE|  
|« Windows » ou « »|« Windows »|« Windows »|non définie|« Windows »|TRUE|  
|« WindowsForms »|« WindowsForms »|« Windows »|TRUE|« Windows »|TRUE|  
|« WindowsFormsWithCustomSubMain »|« Console »|« Windows »|TRUE|« Windows »|TRUE|  
  
 Par défaut, les constantes de compilation conditionnelle non définis résolvent `FALSE`. Vous pouvez spécifier des valeurs pour les constantes non définies lors de la compilation de votre projet pour substituer le comportement par défaut.  
  
> [!NOTE]
>  Lors de la `_MYTYPE` a la valeur « Custom », le projet contient le `My` espace de noms, mais il ne contient aucun objet. Toutefois, l’affectation `_MYTYPE` à « Vide » empêche le compilateur d’ajouter le `My` espace de noms et ses objets.  
  
 Ce tableau décrit les effets des valeurs prédéfinies de la `_MY` des constantes de compilation.  
  
|Constante|Signification|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Permet de `My.Application`, si la constante est « Console », Windows, » ou « WindowsForms » :<br /><br /> -La version « Console » dérive <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>.</xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> et a moins de membres que la version « Windows ».<br />-La version « Windows » dérive <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>et a moins de membres que la version « WindowsForms ».</xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase><br />-La version « WindowsForms » de `My.Application` dérive <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> Si le `TARGET` constante est définie pour être « winexe », puis la classe comprend un `Sub Main` (méthode).|  
|`_MYCOMPUTERTYPE`|Permet de `My.Computer`, si la constante est « Web » ou « Windows » :<br /><br /> -La version « Web » est dérivée de <xref:Microsoft.VisualBasic.Devices.ServerComputer>, et a moins de membres que la version « Windows ».</xref:Microsoft.VisualBasic.Devices.ServerComputer><br />-La version « Windows » de `My.Computer` dérive <xref:Microsoft.VisualBasic.Devices.Computer>.</xref:Microsoft.VisualBasic.Devices.Computer>|  
|`_MYFORMS`|Permet de `My.Forms`, si la constante est `TRUE`.|  
|`_MYUSERTYPE`|Permet de `My.User`, si la constante est « Web » ou « Windows » :<br /><br /> -La version « Web » de `My.User` est associé à l’identité de la requête HTTP actuelle.<br />-La version « Windows » de `My.User` associé au principal actuel du thread.|  
|`_MYWEBSERVICES`|Permet de `My.WebServices`, si la constante est `TRUE`.|  
|`_MYTYPE`|Permet de `My.Log`, `My.Request`, et `My.Response`, si la constante est « Web ».|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer></xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.Logging.Log></xref:Microsoft.VisualBasic.Logging.Log>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User></xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [Comment My dépend du Type de projet](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)   
 [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)   
 [My.Forms, objet](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.Request, objet](../../../visual-basic/language-reference/objects/my-request-object.md)   
 [My.Response, objet](../../../visual-basic/language-reference/objects/my-response-object.md)   
 [My.WebServices (objet)](../../../visual-basic/language-reference/objects/my-webservices-object.md)
