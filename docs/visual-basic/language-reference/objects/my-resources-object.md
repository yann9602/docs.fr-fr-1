---
title: "My.Resources Object | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "My.Resources"
  - "My.Resources.MyResources.ResourceManager"
  - "My.Resources.MyResources.Culture"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Resources object"
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# My.Resources Object
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Fournit des propriétés et des classes pour accéder aux ressources de l'application.  
  
## Notes  
 L'objet `My.Resources` fournit l'accès aux ressources de l'application et vous permet de récupérer de manière dynamique des ressources pour votre application.  Pour plus d'informations, consultez [Gestion des ressources d'une application \(.NET\)](/visual-studio/ide/managing-application-resources-dotnet).  
  
 L'objet `My.Resources` expose uniquement des ressources globales.  Il ne fournit pas l'accès aux fichiers de ressources associés aux formulaires.  Vous devez accéder aux ressources du formulaire à partir du formulaire.  Pour plus d'informations, consultez [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/fr-fr/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
 Vous pouvez accéder aux fichiers de ressources propres à la culture de l'application à partir de l'objet `My.Resources`.  Par défaut, l'objet `My.Resources` recherche des ressources dans le fichier de ressources correspondant à la culture dans la propriété <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>.  Toutefois, vous pouvez substituer ce comportement et spécifier une culture particulière à utiliser pour les ressources.  Pour plus d'informations, consultez [Ressources dans des applications de bureau](../Topic/Resources%20in%20Desktop%20Apps.md).  
  
## Propriétés  
 Les propriétés de l'objet `My.Resources` fournissent un accès en lecture seule aux ressources de votre application.  Pour ajouter ou supprimer des ressources, utilisez le **Concepteur de projets**.  Pour plus d'informations, consultez [How to: Add or Remove Resources](http://msdn.microsoft.com/fr-fr/7b77bc06-3952-4799-b029-def3f8f7f88d).  Vous pouvez accéder aux ressources ajoutées par l'intermédiaire du **Concepteur de projets** à l'aide de `My.Resources.``resourceName`.  
  
 Vous pouvez également ajouter ou supprimer des fichiers de ressources en sélectionnant votre projet dans l'**Explorateur de solutions** et en cliquant sur **Ajouter un nouvel élément** ou sur **Ajouter un élément existant** dans le menu **Projet**.  Vous pouvez accéder aux ressources ajoutées de cette manière en utilisant `My.Resources.``resourceFileName`.`resourceName`.  
  
 Chaque ressource a un nom, une catégorie et une valeur, et ces paramètres de ressources déterminent l'affichage de la propriété qui accède à la ressource dans l'objet `My.Resources`.  Pour les ressources ajoutées dans le **Concepteur de projets** :  
  
-   Le nom détermine le nom de la propriété,  
  
-   Les données de ressources représentent la valeur de la propriété,  
  
-   La catégorie détermine le type de la propriété :  
  
|||  
|-|-|  
|Catégorie|Type de données de la propriété|  
|**Chaînes**|[Chaîne](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**Images**|<xref:System.Drawing.Bitmap>|  
|**Icônes**|<xref:System.Drawing.Icon>|  
|**Audio**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> La classe <xref:System.IO.UnmanagedMemoryStream> dérivant de la classe <xref:System.IO.Stream>, elle peut être utilisée avec les méthodes qui acceptent les flux, par exemple la méthode <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>.|  
|**Fichiers**|-   [String](../../../visual-basic/language-reference/data-types/string-data-type.md) pour les fichiers texte.<br />-   <xref:System.Drawing.Bitmap> pour les fichiers image.<br />-   <xref:System.Drawing.Icon> pour les fichiers icône.<br />-   <xref:System.IO.UnmanagedMemoryStream> pour les fichiers audio.|  
|**Autre**|Déterminé par les informations contenues dans la colonne **Type** du concepteur.|  
  
## Classes  
 L'objet `My.Resources` expose chaque fichier de ressources comme une classe contenant des propriétés partagées.  Le nom de la classe est identique à celui du fichier de ressources.  Comme indiqué dans la section précédente, les ressources contenues dans un fichier de ressources sont exposées comme des propriétés de la classe.  
  
## Exemple  
 Cet exemple définit le titre d'un formulaire la ressource de type chaîne nommée `Form1Title` dans le fichier de ressources de l'application.  Pour que l'exemple fonctionne, l'application doit avoir une chaîne nommée `Form1Title` dans son fichier de ressources.  Pour plus d'informations, consultez [How to: Add or Remove Resources](http://msdn.microsoft.com/fr-fr/7b77bc06-3952-4799-b029-def3f8f7f88d).  
  
 [!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## Exemple  
 Cet exemple affecte à l'icône du formulaire l'icône nommée `Form1Icon` qui est enregistrée dans le fichier de ressources de l'application.  Pour que l'exemple fonctionne, l'application doit avoir une icône nommée `Form1Icon` dans son fichier de ressources.  
  
 [!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## Exemple  
 Cet exemple affecte l'image d'arrière\-plan d'un formulaire à la ressource d'image nommée `Form1Background`, qui se trouve dans le fichier de ressources de l'application.  Pour que cet exemple fonctionne, l'application doit avoir une ressource d'image nommée `Form1Background` dans son fichier de ressources.  
  
 [!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## Exemple  
 Cet exemple lit le son stocké comme une ressource audio nommée `Form1Greeting` dans le fichier de ressources de l'application.  Pour que l'exemple fonctionne, l'application doit avoir une ressource audio nommée `Form1Greeting` dans son fichier de ressources.  La méthode `My.Computer.Audio.Play` n'est disponible que pour les applications Windows Forms.  
  
 [!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## Exemple  
 Cet exemple récupère la version de culture française d'une ressource de type chaîne de l'application.  la ressource est nommée `Message`.  pour modifier la culture que les utilisations d'objet d' `My.Resources` , l'exemple utilise <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.  
  
 Pour que cet exemple fonctionne, l'application doit avoir une chaîne nommée `Message` dans son fichier de ressources, et l'application doit utiliser la version de culture française de ce fichier de ressources, Resources.fr\-FR.resx.  Pour plus d'informations, consultez [How to: Add or Remove Resources](http://msdn.microsoft.com/fr-fr/7b77bc06-3952-4799-b029-def3f8f7f88d).  Si l'application n'a pas la version de culture française du fichier de ressources, l'objet d' `My.Resource` récupère la ressource du fichier de ressources de la culture par défaut.  
  
 [!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## Voir aussi  
 [How to: Add or Remove Resources](http://msdn.microsoft.com/fr-fr/7b77bc06-3952-4799-b029-def3f8f7f88d)   
 [Gestion des ressources d'une application \(.NET\)](/visual-studio/ide/managing-application-resources-dotnet)   
 [Ressources dans des applications de bureau](../Topic/Resources%20in%20Desktop%20Apps.md)   
 [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/fr-fr/9a96220d-a19b-4de0-9f48-01e5d82679e5)