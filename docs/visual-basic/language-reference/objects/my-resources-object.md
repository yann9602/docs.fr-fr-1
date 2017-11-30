---
title: My.Resources, objet
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords: My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b2a2de7229f59e7deea29fe4186a5e466459d9fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="myresources-object"></a>My.Resources, objet
Fournit des propriétés et des classes pour accéder aux ressources de l’application.  
  
## <a name="remarks"></a>Remarques  
 Le `My.Resources` objet fournit l’accès aux ressources de l’application et vous permet de manière dynamique récupérer des ressources pour votre application. Pour plus d’informations, consultez [ressources de gestion de l’Application (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 Le `My.Resources` objet expose uniquement les ressources globales. Il ne fournit pas d’accès aux fichiers de ressources associés aux formulaires. Vous devez accéder à des ressources du formulaire à partir du formulaire. Pour plus d’informations, consultez [Procédure pas à pas : localisation de Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
 Vous pouvez accéder à des fichiers de ressources spécifiques à la culture de l’application à partir de la `My.Resources` objet. Par défaut, le `My.Resources` objet recherche des ressources dans le fichier de ressources qui correspond à la culture dans le <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> propriété. Toutefois, vous pouvez substituer ce comportement et spécifier une culture particulière à utiliser pour les ressources. Pour plus d’informations, consultez [Ressources dans les applications de bureau](../../../framework/resources/index.md).  
  
## <a name="properties"></a>Propriétés  
 Les propriétés de la `My.Resources` objet fournissent un accès en lecture seule aux ressources de votre application. Pour ajouter ou supprimer des ressources, utilisez le **Concepteur de projet**. Pour plus d’informations, consultez [Comment : ajouter ou supprimer des ressources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d). Vous pouvez accéder à des ressources ajoutées via la **Concepteur de projets** à l’aide de `My.Resources.``resourceName`.  
  
 Vous pouvez également ajouter ou supprimer des fichiers de ressources en sélectionnant votre projet dans **l’Explorateur de solutions** et en cliquant sur **ajouter un nouvel élément** ou **ajouter un élément existant** à partir de la  **Projet** menu. Vous pouvez accéder à des ressources ajoutées de cette manière, à l’aide de `My.Resources.``resourceFileName`.`resourceName`.  
  
 Chaque ressource a un nom, la catégorie et la valeur, et ces paramètres de ressources déterminent la façon dont la propriété pour accéder à la ressource s’affiche dans le `My.Resources` objet. Pour les ressources ajoutées dans le **Concepteur de projets**:  
  
-   Le nom détermine le nom de la propriété,  
  
-   Les données de ressources sont la valeur de la propriété,  
  
-   La catégorie détermine le type de la propriété :  
  
|Catégorie|Type de données de propriété|  
|---|---|  
|**Chaînes**|[String](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**Images**|<xref:System.Drawing.Bitmap>|  
|**Icônes**|<xref:System.Drawing.Icon>|  
|**Audio**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> Le <xref:System.IO.UnmanagedMemoryStream> classe dérive de la <xref:System.IO.Stream> classe, donc il peut être utilisé avec des méthodes qui acceptent les flux, telles que le <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> (méthode).|  
|**Fichiers**|-   [Chaîne](../../../visual-basic/language-reference/data-types/string-data-type.md) pour les fichiers texte.<br />-   <xref:System.Drawing.Bitmap>pour les fichiers image.<br />-   <xref:System.Drawing.Icon>pour les fichiers d’icône.<br />-   <xref:System.IO.UnmanagedMemoryStream>pour les fichiers audio.|  
|**Autre**|Déterminé par les informations contenues dans le Concepteur de la **Type** colonne.|  
  
## <a name="classes"></a>Classes  
 Le `My.Resources` objet expose chaque fichier de ressources comme une classe contenant des propriétés partagées. Le nom de classe est le même que le nom du fichier de ressources. Comme décrit dans la section précédente, les ressources dans un fichier de ressources sont exposées comme propriétés de la classe.  
  
## <a name="example"></a>Exemple  
 Cet exemple définit le titre d’un formulaire à la ressource de chaîne nommée `Form1Title` dans le fichier de ressources d’application. Pour l’exemple fonctionne, l’application doit avoir une chaîne nommée `Form1Title` dans son fichier de ressources. Pour plus d’informations, consultez [Comment : ajouter ou supprimer des ressources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d).  
  
 [!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## <a name="example"></a>Exemple  
 Cet exemple définit l’icône du formulaire à l’icône nommée `Form1Icon` qui est stocké dans le fichier de ressources de l’application. Pour l’exemple fonctionne, l’application doit avoir une icône nommée `Form1Icon` dans son fichier de ressources.  
  
 [!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## <a name="example"></a>Exemple  
 Cet exemple définit l’image d’arrière-plan d’un formulaire à la ressource d’image nommée `Form1Background`, qui se trouve dans le fichier de ressources d’application. Pour cet exemple fonctionne, l’application doit avoir une ressource d’image nommée `Form1Background` dans son fichier de ressources.  
  
 [!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## <a name="example"></a>Exemple  
 Cet exemple lit le son stocké comme une ressource audio nommée `Form1Greeting` dans le fichier de ressources de l’application. Pour l’exemple fonctionne, l’application doit avoir une ressource audio nommée `Form1Greeting` dans son fichier de ressources. Le `My.Computer.Audio.Play` méthode est disponible uniquement pour les applications Windows Forms.  
  
 [!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## <a name="example"></a>Exemple  
 Cet exemple récupère la version de la culture Français d’une ressource de chaîne de l’application. La ressource est nommée `Message`. Pour modifier la culture qui le `My.Resources` objet utilise, l’exemple utilise <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.  
  
 Pour cet exemple fonctionne, l’application doit avoir une chaîne nommée `Message` dans sa ressource de fichier et l’application doivent avoir la version de la culture Français de ce fichier de ressources, Resources.fr-fr.resx. Pour plus d’informations, consultez [Comment : ajouter ou supprimer des ressources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d). Si l’application n’a pas la version de la culture Français du fichier de ressources, le `My.Resource` objet récupère la ressource à partir du fichier de ressources de culture par défaut.  
  
 [!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour ajouter ou supprimer des ressources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)  
 [Gestion des ressources d’une application (.NET)](/visualstudio/ide/managing-application-resources-dotnet)  
 [Ressources dans des applications de bureau](../../../framework/resources/index.md)  
 [Procédure pas à pas : Localisation de Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)
