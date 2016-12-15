---
title: "How My Depends on Project Type (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "_MYTYPE"
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How My Depends on Project Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`My` expose uniquement les objets requis par un type de projet particulier.  Par exemple, l'objet `My.Forms` est disponible dans une application Windows Forms et non dans une application console.  Cette rubrique décrit les objets `My` qui sont disponibles dans différents types de projet.  
  
## My dans les applications Windows et les sites Web  
 `My` expose uniquement les objets qui sont utiles dans le type de projet actuel ; il supprime ceux qui sont non applicables.  Par exemple, l'image suivante affiche le modèle d'objet `My` dans un projet Windows Forms.  
  
 ![Forme de My dans une application Windows Forms](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 Dans un projet de site Web, `My` expose les objets qui concernent un développeur Web \(tel que les objets `My.Request` et `My.Response`\) en supprimant ceux qui ne le sont pas \(tels que l'objet `My.Forms`\).  L'image suivante affiche le modèle d'objet `My` dans un projet de site Web :  
  
 ![Forme de My dans une application web](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## Détails du projet  
 Le tableau suivant affiche les objets `My` qui sont activés par défaut pour huit types de projet : application Windows, bibliothèque de classes, application console, bibliothèque de contrôles Windows, bibliothèque de contrôles Web, service Windows, vide et site Web.  
  
 Il existe trois versions de l'objet `My.Application`, deux versions de l'objet `My.Computer` et deux versions de l'objet `My.User`. Les détails de ces versions sont fournis dans les notes de bas de page après le tableau.  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|Objet My|Application Windows|Bibliothèque de classes|Application console|Bibliothèque de contrôles Windows|Bibliothèque de contrôles Web|Service Windows|Vide|Site Web|  
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
  
 <sup>1</sup> Version Windows Forms de `My.Application`.  Dérive de la version de la console \(voir Remarque 3\), ajoute une prise en charge pour interagir avec les fenêtres de l'application et fournit le modèle d'application [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 <sup>2</sup> Version de bibliothèque de `My.Application`.  Fournit les fonctionnalités de base requises par une application : fournit des membres pour l'écriture dans le journal des applications et l'accès aux informations de cette dernière.  
  
 <sup>3</sup> Version de console de `My.Application`.  Dérive de la version de la bibliothèque \(voir Remarque 2\) et ajoute des membres supplémentaires pour accéder aux arguments de ligne de commande de l'application et aux informations de déploiement ClickOnce.  
  
 <sup>4</sup> Version Windows de `My.Computer`.  Dérive de la version du serveur \(voir Remarque 5\) et fournit l'accès aux objets utiles d'un ordinateur client, tels que le clavier, l'écran et la souris.  
  
 <sup>5</sup> Version du serveur de `My.Computer`.  Fournit des informations de base sur l'ordinateur, tels que le nom, l'accès à l'horloge, etc.  
  
 <sup>6</sup> Version Windows de `My.User`.  Cet objet est associé à l'identité actuelle du thread.  
  
 <sup>7</sup> Version Web de `My.User`.  Cet objet est associé à l'identité de l'utilisateur de la demande HTTP actuelle de l'application.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.Logging.Log>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [\/define](../../../visual-basic/reference/command-line-compiler/define.md)   
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.Request Object](../../../visual-basic/language-reference/objects/my-request-object.md)   
 [My.Response Object](../../../visual-basic/language-reference/objects/my-response-object.md)   
 [My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)