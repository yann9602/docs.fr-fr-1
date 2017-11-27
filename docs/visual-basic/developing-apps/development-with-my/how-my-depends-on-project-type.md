---
title: "Comment My dépend du type de projet (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a37bf43096931597278974099becb9be6ae133d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>Comment My dépend du type de projet (Visual Basic)
`My`expose uniquement les objets requis par un type de projet particulier. Par exemple, le `My.Forms` objet est disponible dans une application Windows Forms et non dans une application console. Cette rubrique explique ce qui `My` objets sont disponibles dans différents types de projet.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>Mon Windows dans les Applications et Sites Web  
 `My`expose uniquement les objets qui sont utiles dans le type de projet actuel ; Il supprime les objets qui ne sont pas applicables. Par exemple, l’illustration suivante montre la `My` modèle objet dans un projet Windows Forms.  
  
 ![Forme de My dans une application Windows Forms](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 Dans un projet de site Web, `My` expose les objets qui correspondent à un développeur Web (telles que la `My.Request` et `My.Response` objets) lors de la suppression des objets qui ne sont pas pertinents (tels que le `My.Forms` objet). L’illustration suivante montre la `My` modèle objet dans un projet de site Web :  
  
 ![Forme de My dans une application Web](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## <a name="project-details"></a>Détails du projet  
 Le tableau suivant indique les `My` objets activés par défaut pour huit types de projet : application Windows, bibliothèque de classes, application console, bibliothèque de contrôles Windows, bibliothèque de contrôles Web, service Windows, vide et site Web.  
  
 Il existe trois versions de la `My.Application` (objet), les deux versions de la `My.Computer` objet et les deux versions de `My.User` de l’objet ; plus d’informations sur ces versions sont fournies dans les pieds de page après le tableau.  
  
|My (objet)|Application Windows|Bibliothèque de classes|Application console|Bibliothèque de contrôles Windows|Bibliothèque de contrôles Web|Service Windows|Empty|Site web|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**Oui** <sup>1</sup>|**Oui** <sup>2</sup>|**Oui** <sup>3</sup>|**Oui** <sup>2</sup>|Non|**Oui** <sup>3</sup>|Non|Non|  
|`My.Computer`|**Oui** <sup>4</sup>|**Oui** <sup>4</sup>|**Oui** <sup>4</sup>|**Oui** <sup>4</sup>|**Oui** <sup>5</sup>|**Oui** <sup>4</sup>|Non|**Oui** <sup>5</sup>|  
|`My.Forms`|**Oui**|Non|Non|**Oui**|Non|Non|Non|Non|  
|`My.Log`|Non|Non|Non|Non|Non|Non|Non|**Oui**|  
|`My.Request`|Non|Non|Non|Non|Non|Non|Non|**Oui**|  
|`My.Resources`|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|Non|Non|  
|`My.Response`|Non|Non|Non|Non|Non|Non|Non|**Oui**|  
|`My.Settings`|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|Non|Non|  
|`My.User`|**Oui** <sup>6</sup>|**Oui** <sup>6</sup>|**Oui** <sup>6</sup>|**Oui** <sup>6</sup>|**Oui** <sup>7</sup>|**Oui** <sup>6</sup>|Non|**Oui** <sup>7</sup>|  
|`My.WebServices`|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|**Oui**|Non|Non|  
  
 <sup>1</sup> version Windows Forms de `My.Application`. Dérive de la version de la console (voir Remarque 3) ; Ajoute la prise en charge pour interagir avec les fenêtres de l’application et fournit le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] modèle d’Application.  
  
 <sup>2</sup> version de la bibliothèque de `My.Application`. Fournit les fonctionnalités de base requises par une application : fournit des membres pour l’écriture dans le journal des applications et l’accès aux informations de l’application.  
  
 <sup>3</sup> version de la console de `My.Application`. Dérive de la version de la bibliothèque (voir Remarque 2), et ajoute des membres supplémentaires pour accéder aux arguments de ligne de commande de l’application et les informations de déploiement ClickOnce.  
  
 <sup>4</sup> version Windows de `My.Computer`. Dérive de la version du serveur (voir Remarque 5) et fournit l’accès aux objets utiles sur un ordinateur client, telles que le clavier, écran et la souris.  
  
 <sup>5</sup> version du serveur de `My.Computer`. Fournit des informations de base sur l’ordinateur, telles que le nom, l’accès à l’horloge et ainsi de suite.  
  
 <sup>6</sup> version Windows de `My.User`. Cet objet est associé à l’identité du thread actuel.  
  
 <sup>7</sup> version web de `My.User`. Cet objet est associé à l’identité de la requête HTTP actuelle de l’application.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.Logging.Log>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [Personnalisation de la disponibilité ou non des objets dans My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [My.Forms (objet)](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [My.Request (objet)](../../../visual-basic/language-reference/objects/my-request-object.md)  
 [My.Response (objet)](../../../visual-basic/language-reference/objects/my-response-object.md)  
 [My.WebServices (objet)](../../../visual-basic/language-reference/objects/my-webservices-object.md)
