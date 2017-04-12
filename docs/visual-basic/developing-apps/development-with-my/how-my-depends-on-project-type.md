---
title: "Comment My dépend du Type de projet (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
caps.latest.revision: 18
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
ms.openlocfilehash: d193dade94980f04b31605ea6fa968f9fa7d0ad6
ms.lasthandoff: 03/13/2017

---
# <a name="how-my-depends-on-project-type-visual-basic"></a>Comment My dépend du type de projet (Visual Basic)
`My`expose uniquement les objets requis par un type de projet particulier. Par exemple, le `My.Forms` objet est disponible dans une application Windows Forms et non dans une application console. Cette rubrique décrit ce qui `My` les objets sont disponibles dans différents types de projets.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>Mon Windows dans les Applications et Sites Web  
 `My`expose uniquement les objets qui sont utiles dans le type de projet en cours ; Il supprime tous les objets qui ne sont pas applicables. Par exemple, l’illustration suivante montre la `My` modèle d’objet dans un projet Windows Forms.  
  
 ![Forme de My dans une application Windows Forms](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 Dans un projet de site Web, `My` expose les objets qui concernent un développeur Web (tel que le `My.Request` et `My.Response` objets) en supprimant ceux qui n’est pas pertinentes (tels que le `My.Forms` objet). L’illustration suivante montre la `My` modèle d’objet dans un projet de site Web :  
  
 ![Forme de My dans une application Web](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## <a name="project-details"></a>Détails du projet  
 Le tableau suivant indique les `My` objets sont activés par défaut pour huit types de projet : application Windows, bibliothèque de classes, application console, bibliothèque de contrôles Windows, bibliothèque de contrôles Web, service Windows, vide et site Web.  
  
 Il existe trois versions de la `My.Application` (objet), les deux versions de la `My.Computer` objet et deux versions de `My.User` de l’objet ; plus d’informations sur ces versions sont fournis dans les notes de bas de page après le tableau.  
  
|My (objet)|Application Windows|Bibliothèque de classes|Application console|Bibliothèque de contrôles Windows|Bibliothèque de contrôles web|Service Windows|Empty|Site web|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**Yes** <sup>1</sup>|**Yes** <sup>2</sup>|**Yes** <sup>3</sup>|**Yes** <sup>2</sup>|Non|**Yes** <sup>3</sup>|Non|Non|  
|`My.Computer`|**Yes** <sup>4</sup>|**Yes** <sup>4</sup>|**Yes** <sup>4</sup>|**Yes** <sup>4</sup>|**Yes** <sup>5</sup>|**Yes** <sup>4</sup>|Non|**Yes** <sup>5</sup>|  
|`My.Forms`|**Oui**|Non|Non|**Oui**|Non|Non|Non|Non|  
|`My.Log`|Non|Non|Non|Non|Non|Non|Non|**Oui**|  
|`My.Request`|Non|Non|Non|Non|Non|Non|Non|**Oui**|  
|`My.Resources`|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|Non|Non|  
|`My.Response`|Non|Non|Non|Non|Non|Non|Non|**Oui**|  
|`My.Settings`|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|Non|Non|  
|`My.User`|**Yes** <sup>6</sup>|**Yes** <sup>6</sup>|**Yes** <sup>6</sup>|**Yes** <sup>6</sup>|**Yes** <sup>7</sup>|**Yes** <sup>6</sup>|Non|**Yes** <sup>7</sup>|  
|`My.WebServices`|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|Non|Non|  
  
 <sup>1</sup> version Windows Forms de `My.Application`. Dérive de la version de la console (voir Remarque 3) ; Ajoute la prise en charge pour interagir avec les fenêtres de l’application et fournit le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] modèle d’Application.  
  
 <sup>2</sup> de version de la bibliothèque `My.Application`. Fournit les fonctionnalités de base requises par une application : fournit des membres pour l’écriture dans le journal des applications et l’accès aux informations de l’application.  
  
 <sup>3</sup> version de console de `My.Application`. Dérive de la version de la bibliothèque (voir Remarque 2), et ajoute des membres supplémentaires pour accéder aux arguments de ligne de commande et les informations de déploiement ClickOnce de l’application.  
  
 <sup>4</sup> version Windows de `My.Computer`. Dérive de la version du serveur (voir Remarque 5) et fournit l’accès aux objets utiles sur un ordinateur client, tels que le clavier, écran et souris.  
  
 <sup>5</sup> version du serveur de `My.Computer`. Fournit des informations de base sur l’ordinateur, telles que le nom, l’accès à l’horloge et ainsi de suite.  
  
 <sup>6</sup> version Windows de `My.User`. Cet objet est associé à l’identité du thread actuel.  
  
 <sup>7</sup> version web de `My.User`. Cet objet est associé à l’identité de la requête HTTP actuelle de l’application.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer></xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.Logging.Log></xref:Microsoft.VisualBasic.Logging.Log>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User></xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [Personnalisation des objets sont disponibles dans ma](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)   
 [My.Forms, objet](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.Request, objet](../../../visual-basic/language-reference/objects/my-request-object.md)   
 [My.Response, objet](../../../visual-basic/language-reference/objects/my-response-object.md)   
 [My.WebServices (objet)](../../../visual-basic/language-reference/objects/my-webservices-object.md)
