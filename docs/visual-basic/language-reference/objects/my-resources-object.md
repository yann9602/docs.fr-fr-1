---
title: My.Resources (objet) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
dev_langs:
- VB
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: 22
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 6ad5bd4e33438256719b59cb0936cf6bc8525ab1
ms.lasthandoff: 03/13/2017

---
# <a name="myresources-object"></a>My.Resources, objet
Fournit des propriétés et des classes permettant d’accéder aux ressources de l’application.  
  
## <a name="remarks"></a>Remarques  
 Le `My.Resources` objet fournit l’accès aux ressources de l’application et vous permet de récupérer des ressources pour votre application. Pour plus d’informations, consultez [ressources de gestion de l’Application (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet).  
  
 Le `My.Resources` objet expose uniquement les ressources globales. Il ne donne pas accès aux fichiers de ressources associés aux formulaires. Vous devez accéder à des ressources du formulaire à partir du formulaire. Pour plus d’informations, consultez [Procédure pas à pas : localisation de Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
 Vous pouvez accéder à des fichiers de ressources spécifiques à la culture de l’application à partir de la `My.Resources` objet. Par défaut, le `My.Resources` objet recherche des ressources dans le fichier de ressources correspondant à la culture dans le <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>propriété.</xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> Toutefois, vous pouvez substituer ce comportement et spécifier une culture particulière à utiliser pour les ressources. Pour plus d’informations, consultez [des ressources dans les applications de bureau](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890).  
  
## <a name="properties"></a>Propriétés  
 Les propriétés de la `My.Resources` objet fournit un accès en lecture seule aux ressources de votre application. Pour ajouter ou supprimer des ressources, utilisez le **Concepteur de projet**. Pour plus d’informations, consultez [Comment : ajouter ou supprimer des ressources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d). Vous pouvez accéder aux ressources ajoutées via la **Concepteur de projet** à l’aide de `My.Resources.``resourceName`.  
  
 Vous pouvez également ajouter ou supprimer des fichiers de ressources en sélectionnant votre projet dans **l’Explorateur de solutions** et en cliquant sur **ajouter un nouvel élément** ou **ajouter un élément existant** à partir de la **projet** menu. Vous pouvez accéder à des ressources ajoutées de cette manière, à l’aide de `My.Resources.``resourceFileName`.`resourceName`.  
  
 Chaque ressource a un nom, une catégorie et une valeur, et ces paramètres de ressources déterminent comment la propriété pour accéder à la ressource dans le `My.Resources` objet. Pour les ressources ajoutées dans le **Concepteur de projet**:  
  
-   Le nom détermine le nom de la propriété,  
  
-   Les données de ressources sont la valeur de la propriété,  
  
-   La catégorie détermine le type de la propriété :  
  
|Catégorie|Type de données de propriété|  
|---|---|  
|**Chaînes**|[String](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**Images**|<xref:System.Drawing.Bitmap></xref:System.Drawing.Bitmap>|  
|**Icônes**|<xref:System.Drawing.Icon></xref:System.Drawing.Icon>|  
|**Audio**|<xref:System.IO.UnmanagedMemoryStream></xref:System.IO.UnmanagedMemoryStream><br /><br /> La <xref:System.IO.UnmanagedMemoryStream>classe dérive de la <xref:System.IO.Stream>classe, donc il peut être utilisé avec des méthodes qui acceptent les flux, tels que le <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>(méthode).</xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> </xref:System.IO.Stream> </xref:System.IO.UnmanagedMemoryStream>|  
|**Fichiers**|-   [Chaîne](../../../visual-basic/language-reference/data-types/string-data-type.md) pour les fichiers texte.<br />- <xref:System.Drawing.Bitmap>pour les fichiers image.</xref:System.Drawing.Bitmap><br />- <xref:System.Drawing.Icon>pour les fichiers icône.</xref:System.Drawing.Icon><br />- <xref:System.IO.UnmanagedMemoryStream>pour les fichiers audio.</xref:System.IO.UnmanagedMemoryStream>|  
|**Autre**|Déterminé par les informations contenues dans le Concepteur de la **Type** colonne.|  
  
## <a name="classes"></a>Classes  
 Le `My.Resources` objet expose chaque fichier de ressources comme une classe contenant des propriétés partagées. Le nom de classe est le même que le nom du fichier de ressources. Comme décrit dans la section précédente, les ressources dans un fichier de ressources sont exposées comme propriétés de la classe.  
  
## <a name="example"></a>Exemple  
 Cet exemple définit le titre d’un formulaire à la ressource de chaîne nommée `Form1Title` dans le fichier de ressources d’application. Pour l’exemple fonctionne, l’application doit avoir une chaîne nommée `Form1Title` dans son fichier de ressources. Pour plus d’informations, consultez [Comment : ajouter ou supprimer des ressources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d).  
  
 [!code-vb[VbVbalrMyResources n °&1;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## <a name="example"></a>Exemple  
 Cet exemple définit l’icône du formulaire l’icône nommée `Form1Icon` qui est stocké dans le fichier de ressources. Pour l’exemple fonctionne, l’application doit avoir une icône nommée `Form1Icon` dans son fichier de ressources.  
  
 [!code-vb[VbVbalrMyResources n °&2;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## <a name="example"></a>Exemple  
 Cet exemple définit l’image d’arrière-plan d’un formulaire à la ressource d’image nommée `Form1Background`, qui est dans le fichier de ressources d’application. Pour cet exemple fonctionne, l’application doit avoir une ressource d’image nommée `Form1Background` dans son fichier de ressources.  
  
 [!code-vb[VbVbalrMyResources n °&3;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## <a name="example"></a>Exemple  
 Cet exemple lit le son stocké comme une ressource audio nommée `Form1Greeting` dans le fichier de ressources. Pour l’exemple fonctionne, l’application doit avoir une ressource audio nommée `Form1Greeting` dans son fichier de ressources. Le `My.Computer.Audio.Play` méthode est disponible uniquement pour les applications Windows Forms.  
  
 [!code-vb[VbVbalrMyResources n °&4;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## <a name="example"></a>Exemple  
 Cet exemple récupère la version de la culture Français d’une ressource de chaîne de l’application. La ressource est nommée `Message`. Pour modifier la culture que le `My.Resources` utilise de l’objet, l’exemple utilise <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.</xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>  
  
 Pour cet exemple fonctionne, l’application doit avoir une chaîne nommée `Message` dans sa ressource de fichier et l’application doivent avoir la version de la culture Français de ce fichier de ressources, Resources.fr-fr.resx. Pour plus d’informations, consultez [Comment : ajouter ou supprimer des ressources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d). Si l’application n’a pas la version de la culture Français du fichier de ressources, le `My.Resource` objet récupère la ressource à partir du fichier de ressources de culture par défaut.  
  
 [!code-vb[VbVbalrMyResources&#10;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : ajouter ou supprimer des ressources](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)   
 [La gestion des ressources d’Application (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet)   
 [Ressources dans les applications de bureau](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)   
 [Procédure pas à pas : Localisation de Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)
