---
title: "My.Forms Object | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "My.Forms"
  - "My.MyProject.Forms"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Forms object"
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# My.Forms Object
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Fournit des propriétés permettant d'accéder à une instance de chaque formulaire Windows déclaré dans le projet actuel.  
  
## Notes  
 L'objet `My.Forms` fournit une instance de chaque formulaire dans le projet actuel.  La propriété porte le même que celui du formulaire auquel la propriété accède.  Pour plus d'informations sur l'ajout de formulaires à un projet, consultez [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/fr-fr/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
 Vous pouvez accéder aux formulaires fournis par l'objet `My.Forms` à l'aide du nom du formulaire, sans qualification.  Étant donné que la propriété porte le même nom que le nom de type du formulaire, vous pouvez accéder à un formulaire comme s'il avait une instance par défaut.  Par exemple, `My.Forms.Form1.Show` est équivalent à `Form1.Show`.  
  
 L'objet `My.Forms` n'expose que les formulaires associés au projet actuel.  Il ne fournit pas un accès aux formulaires déclarés dans les DLL référencées.  Pour accéder à un formulaire fourni par une DLL, vous devez utiliser le nom qualifié du formulaire, écrit sous la forme *DllName*.*FormName*.  
  
 Vous pouvez utiliser la propriété <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> pour obtenir une collection de tous les formulaires ouverts de l'application.  
  
 L'objet et ses propriétés ne sont disponibles que pour les applications Windows.  
  
## Propriétés  
 Chaque propriété de l'objet `My.Forms` fournit l'accès à une instance d'un formulaire du projet actuel.  La propriété porte le même nom que celui du formulaire auquel accède la propriété et le type de propriété porte le même nom que le type de formulaire.  
  
> [!NOTE]
>  Si une collision de noms se produit, le nom de la propriété pour accéder à un formulaire est *RootNamespace*\_*Namespace*\_*FormName*.  Par exemple, prenons deux formulaires nommés `Form1.`Si l'un de ces formulaires se trouve dans l'espace de noms racine `WindowsApplication1` et dans l'espace de noms `Namespace1`, vous accédez à ce formulaire via `My.Forms.WindowsApplication1_Namespace1_Form1`.  
  
 L'objet `My.Forms` fournit un accès à l'instance du formulaire principal de l'application qui a été créé au démarrage.  Pour tous les autres formulaires, l'objet `My.Forms` crée une instance du formulaire lorsqu'il est ouvert et le stocke.  Les tentatives ultérieures pour accéder à la propriété retournent cette instance du formulaire.  
  
 Vous pouvez supprimer un formulaire en assignant `Nothing` à sa propriété.  L'accesseur Set de la propriété appelle la méthode <xref:System.Windows.Forms.Form.Close%2A> du formulaire, puis assigne `Nothing` à la valeur stockée.  Si vous assignez une valeur autre que `Nothing` à la propriété, l'accesseur Set lève une exception <xref:System.ArgumentException>.  
  
 Vous pouvez tester si une propriété de l'objet `My.Forms` stocke une instance du formulaire à l'aide de l'opérateur `Is` ou `IsNot`.  Vous pouvez utiliser ces opérateurs pour vérifier si la propriété a la valeur `Nothing`.  
  
> [!NOTE]
>  En général, l'opérateur `Is` ou `IsNot` doit lire la valeur de la propriété pour effectuer la comparaison.  Toutefois, si la propriété stocke actuellement `Nothing`, la propriété crée une instance du formulaire, puis la retourne.  Néanmoins, le compilateur Visual Basic traite différemment les propriétés de l'objet `My.Forms` et permet à l'opérateur `Is` ou `IsNot` de vérifier l'état de la propriété sans modifier sa valeur.  
  
## Exemple  
 Cet exemple modifie le titre du formulaire `SidebarMenu` par défaut.  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 Pour que cet exemple fonctionne, votre projet doit avoir un formulaire nommé `SidebarMenu`.  Pour plus d'informations, consultez [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/fr-fr/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
 Ce code ne fonctionne que dans un projet d'application Windows.  
  
## Configuration requise  
  
### Disponibilité par type de projet  
  
|||  
|-|-|  
|Type de projet|Disponible|  
|Application Windows|**Oui**|  
|Bibliothèque de classes|Non|  
|Application console|Non|  
|Bibliothèque de contrôles Windows|Non|  
|Bibliothèque de contrôles Web|Non|  
|Service Windows|Non|  
|Site Web|Non|  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>   
 <xref:System.Windows.Forms.Form>   
 <xref:System.Windows.Forms.Form.Close%2A>   
 [Objects](../../../visual-basic/language-reference/objects/index.md)   
 [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/fr-fr/3d7bb25f-fd90-47cf-9378-fa0d764686c1)   
 [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Accessing Application Forms](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)