---
title: "My.Settings, objet | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "My.MySettingsProperty.Settings"
  - "My.Settings"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Settings (objet)"
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# My.Settings, objet
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Fournit des propriétés et des méthodes pour accéder aux paramètres de l’application.  
  
## <a name="remarks"></a>Notes  
 Le `My.Settings` objet fournit l’accès aux paramètres de l’application et vous permet de stocker et récupérer des paramètres de propriété et d’autres informations pour votre application de manière dynamique. Pour plus d’informations, consultez [paramètres de gestion de l’Application (.NET)](/visual-studio/ide/managing-application-settings-dotnet).  
  
## <a name="properties"></a>Propriétés  
 Les propriétés de la `My.Settings` objet fournit l’accès aux paramètres de votre application. Pour ajouter ou supprimer des paramètres, utilisez le **Concepteur de paramètres**.  
  
 Chaque paramètre a un **nom**, **Type**, **étendue**, et **valeur**, et ces paramètres déterminent la façon dont la propriété qui accède à chaque paramètre apparaît dans les `My.Settings` objet :  
  
-   **Nom** détermine le nom de la propriété.  
  
-   **Type** détermine le type de la propriété.  
  
-   **Étendue** indique si la propriété est en lecture seule. Si la valeur est **Application**, la propriété est en lecture seule ; si la valeur est **utilisateur**, la propriété est en lecture-écriture.  
  
-   **Valeur** est la valeur par défaut de la propriété.  
  
## <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|Méthode|Description|  
|`Reload`|Recharge les paramètres utilisateur à partir des dernières valeurs enregistrées.|  
|`Save`|Enregistre les paramètres utilisateur actuels.|  
  
 Le `My.Settings` objet fournit également des propriétés avancées et des méthodes héritées de la <xref:System.Configuration.ApplicationSettingsBase> (classe).  
  
## <a name="tasks"></a>Tâches  
 Le tableau suivant répertorie des exemples de tâches impliquant la `My.Settings` objet.  
  
|||  
|-|-|  
|Pour|Voir|  
|Lire un paramètre d’application|[Comment : lire des paramètres d’Application dans Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|Modifier un paramètre utilisateur|[Comment : modifier les paramètres utilisateur dans Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|Conserver des paramètres utilisateur|[Comment : rendre persistants les paramètres utilisateur dans Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|Créer une grille de propriétés pour les paramètres utilisateur|[Comment : créer des grilles de propriétés pour les paramètres utilisateur dans Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>Exemple  
 Cet exemple affiche la valeur de le `Nickname` paramètre.  
  
 [!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]  
  
 Pour cet exemple fonctionne, votre application doit avoir un `Nickname` paramètre, de type `String`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Configuration.ApplicationSettingsBase>   
 [Comment : lire des paramètres d’Application dans Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [Comment : modifier les paramètres utilisateur dans Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)   
 [Comment : rendre persistants les paramètres utilisateur dans Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [Comment : créer des grilles de propriétés pour les paramètres utilisateur dans Visual Basic](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [Gestion des paramètres d’Application (.NET)](/visual-studio/ide/managing-application-settings-dotnet)