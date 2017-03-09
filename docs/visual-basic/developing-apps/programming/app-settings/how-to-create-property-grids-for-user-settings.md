---
title: "How to: Create Property Grids for User Settings in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Settings object, creating property grids for user settings"
  - "user settings, creating property grids"
  - "property grids, creating for user settings"
  - "property grids"
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Create Property Grids for User Settings in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez créer une grille de propriétés pour les paramètres utilisateur en remplissant un contrôle <xref:System.Windows.Forms.PropertyGrid> à l'aide des propriétés des paramètres utilisateur de l'objet `My.Settings`.  
  
> [!NOTE]
>  Pour que cet exemple fonctionne, vous devez configurer les paramètres utilisateur de votre application.  Pour plus d’informations, consultez [Gestion des paramètres d'une application \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet).  
  
 L'objet `My.Settings` expose chaque paramètre comme une propriété.  Le nom de la propriété et celui du paramètre sont identiques, de même que le type de propriété et le type de paramètre.  La **Portée** du paramètre détermine si la propriété est en lecture seule : la propriété d'un paramètre de portée **Application** est en lecture seule, tandis que la propriété d'un paramètre de portée **Utilisateur** est en mode lecture\-écriture.  Pour plus d’informations, consultez [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Vous ne pouvez pas modifier ni enregistrer les valeurs des paramètres de portée application au moment de l'exécution.  Les paramètres de portée application ne peuvent être modifiés que lors de la création de l'application \(via le **Concepteur de projets**\) ou de la modification du fichier de configuration de l'application.  Pour plus d’informations, consultez [Gestion des paramètres d'une application \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet).  
  
 Cet exemple utilise un contrôle <xref:System.Windows.Forms.PropertyGrid> pour accéder aux propriétés des paramètres utilisateur de l'objet `My.Settings`.  Par défaut, la <xref:System.Windows.Forms.PropertyGrid> affiche toutes les propriétés de l'objet `My.Settings`.  Toutefois, les propriétés des paramètres utilisateur ont l'attribut <xref:System.Configuration.UserScopedSettingAttribute>.  Cet exemple affecte à la propriété <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> du <xref:System.Windows.Forms.PropertyGrid> la valeur <xref:System.Configuration.UserScopedSettingAttribute> pour afficher uniquement les propriétés des paramètres utilisateur.  
  
### Pour ajouter une grille de propriétés de paramètres utilisateur  
  
1.  Ajoutez le contrôle **PropertyGrid** de la **Boîte à outils** à l'aire de conception de votre application, représentée dans cet exemple par  `Form1`.  
  
     Le nom par défaut du contrôle de la grille de propriétés est `PropertyGrid1`.  
  
2.  Double\-cliquez sur l'aire de conception de `Form1` pour ouvrir le code pour le gestionnaire d'événements de chargement du formulaire.  
  
3.  Définissez l'objet `My.Settings` comme étant l'objet sélectionné pour la grille de propriétés.  
  
     [!code-vb[VbVbalrMyResources#11](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/visualbasic/VbVbalrMyResources2/Form1.vb#11)]  
  
4.  Configurez la grille de propriétés pour afficher uniquement les paramètres utilisateur.  
  
     [!code-vb[VbVbalrMyResources#12](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/visualbasic/VbVbalrMyResources2/Form1.vb#12)]  
  
    > [!NOTE]
    >  Pour afficher uniquement les paramètres de portée application, utilisez l'attribut de <xref:System.Configuration.ApplicationScopedSettingAttribute> au lieu d' <xref:System.Configuration.UserScopedSettingAttribute>.  
  
## Programmation fiable  
 L'application enregistre les paramètres utilisateur lorsqu'elle s'arrête.  Pour enregistrer les paramètres immédiatement, appelez la méthode `My.Settings.Save`.  Pour plus d’informations, consultez [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## Voir aussi  
 [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [How to: Read Application Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [How to: Change User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)   
 [How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [Gestion des paramètres d'une application \(.NET\)](/visual-studio/ide/managing-application-settings-dotnet)