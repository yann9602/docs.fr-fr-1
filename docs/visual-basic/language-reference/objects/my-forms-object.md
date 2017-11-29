---
title: My.Forms, objet
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords: My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a5aa7af1f07a29660335d968c1ecc17be5f8beec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="myforms-object"></a>My.Forms, objet
Fournit des propriétés pour accéder à une instance de chaque Windows form déclaré dans le projet actuel.  
  
## <a name="remarks"></a>Remarques  
 Le `My.Forms` objet fournit une instance de chaque formulaire dans le projet actuel. Le nom de la propriété est le même que le nom du formulaire auquel la propriété accède. Pour plus d’informations sur l’ajout de formes à un projet, consultez [Comment : ajouter des Windows Forms à un projet](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
 Vous pouvez accéder aux écrans fournis par le `My.Forms` objet en utilisant le nom du formulaire, sans qualification. Étant donné que le nom de propriété est identique au nom de type du formulaire, ainsi vous permet d’accéder à un formulaire comme s’il avait une instance par défaut. Par exemple, `My.Forms.Form1.Show` équivaut à `Form1.Show`.  
  
 Le `My.Forms` objet expose uniquement les formulaires associés au projet actuel. Il ne fournit pas d’accès aux formulaires déclarés dans les DLL référencées. Pour accéder à un formulaire par une DLL, vous devez utiliser le nom qualifié du formulaire, écrit sous la forme *DllName*. *Formulaire*.  
  
 Vous pouvez utiliser le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> propriété pour obtenir une collection de formulaires ouverts de toute l’application.  
  
 L’objet et ses propriétés sont disponibles uniquement pour les applications Windows.  
  
## <a name="properties"></a>Propriétés  
 Chaque propriété de la `My.Forms` objet fournit l’accès à une instance d’un formulaire dans le projet actuel. Le nom de la propriété est le même que le nom du formulaire auquel accède la propriété et le type de propriété est le même que le type de formulaire.  
  
> [!NOTE]
>  S’il existe un conflit de noms, le nom de propriété pour accéder à un formulaire est *RootNamespace*_*Namespace*\_*formulaire*. Par exemple, prenons deux formulaires nommés `Form1.`si une de ces formes est dans l’espace de noms racine `WindowsApplication1` et dans l’espace de noms `Namespace1`, vous accédez à ce formulaire via `My.Forms.WindowsApplication1_Namespace1_Form1`.  
  
 Le `My.Forms` objet fournit l’accès à l’instance du formulaire principal de l’application qui a été créé au démarrage. Pour toutes les autres formes, le `My.Forms` objet crée une nouvelle instance du formulaire lorsqu’il est accessible et l’enregistre. Les tentatives suivantes pour accéder à cette propriété retournent cette instance du formulaire.  
  
 Vous pouvez supprimer un formulaire en assignant `Nothing` à la propriété de ce formulaire. Les appels de méthode setter de propriété le <xref:System.Windows.Forms.Form.Close%2A> méthode du formulaire, puis assigne `Nothing` à la valeur stockée. Si vous assignez une valeur autre que `Nothing` à la propriété, la méthode setter lève une <xref:System.ArgumentException> exception.  
  
 Vous pouvez tester si une propriété de la `My.Forms` objet stocke une instance du formulaire à l’aide de la `Is` ou `IsNot` opérateur. Vous pouvez utiliser ces opérateurs pour vérifier si la valeur de la propriété est `Nothing`.  
  
> [!NOTE]
>  En règle générale, les `Is` ou `IsNot` opérateur doit lire la valeur de la propriété pour effectuer la comparaison. Toutefois, si la propriété stocke actuellement `Nothing`, la propriété crée une nouvelle instance de la forme et puis retourne cette instance. Toutefois, le compilateur Visual Basic traite les propriétés de la `My.Forms` différemment de l’objet et permet la `Is` ou `IsNot` opérateur afin de vérifier l’état de la propriété sans modifier sa valeur.  
  
## <a name="example"></a>Exemple  
 Cet exemple modifie le titre de la valeur par défaut `SidebarMenu` formulaire.  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 Pour cet exemple fonctionne, votre projet doit avoir un formulaire nommé `SidebarMenu`. Pour plus d’informations, consultez [Comment : ajouter des Windows Forms à un projet](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
 Ce code ne fonctionne que dans un projet d’Application Windows.  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="availability-by-project-type"></a>Disponibilité par Type de projet  
  
|Type de projet|Disponible|  
|---|---|  
|Application Windows|**Oui**|  
|Bibliothèque de classes|Non|  
|Application console|Non|  
|Bibliothèque de contrôles Windows|Non|  
|Bibliothèque de contrôles Web|Non|  
|Service Windows|Non|  
|Site web|Non|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [Objects](../../../visual-basic/language-reference/objects/index.md)  
 [Comment : ajouter des Windows Forms à un projet](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)  
 [Is (opérateur)](../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot (opérateur)](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Accès aux formulaires de l’application](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
