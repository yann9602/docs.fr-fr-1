---
title: "Développement rapide d'application avec My.Resources et My.Settings (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1657febf935560ff4c8dd2f54b10fdcb2254891f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>Développement rapide d'application avec My.Resources et My.Settings (Visual Basic)
Le `My.Resources` objet fournit l’accès aux ressources de l’application et vous permet de récupérer dynamiquement des ressources pour votre application.  
  
## <a name="retrieving-resources"></a>Récupération de ressources  
 Un nombre de ressources, telles que les fichiers audio, les icônes, les images et les chaînes peut être récupéré via la `My.Resources` objet. Par exemple, vous pouvez accéder les fichiers de ressources spécifiques à la culture de l’application. L’exemple suivant définit l’icône du formulaire à l’icône nommée `Form1Icon` stockées dans le fichier de ressources de l’application.  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 Le `My.Resources` objet expose uniquement les ressources globales. Il ne fournit pas d’accès aux fichiers de ressources associés aux formulaires. Vous devez accéder à des ressources du formulaire à partir du formulaire. Pour plus d’informations, consultez [Procédure pas à pas : localisation de Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
 De même, le `My.Settings` objet fournit l’accès aux paramètres de l’application et vous permet de stocker et récupérer des paramètres de propriété et d’autres informations pour votre application de manière dynamique. Pour plus d’informations, consultez [My.Resources (objet)](../../../visual-basic/language-reference/objects/my-resources-object.md) et [My.Settings (objet)](../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Voir aussi  
 [My.Resources (objet)](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [My.Settings (objet)](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Accès aux paramètres d’application](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)
