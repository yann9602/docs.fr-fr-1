---
title: Exemple de classe COM (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a759a7dcd211207c8740dd99d592daa509ddec47
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="example-com-class-c-programming-guide"></a>Exemple de classe COM (Guide de programmation C#)
Voici un exemple de classe pouvant être exposée en tant qu’objet COM. Après avoir placé ce code dans un fichier .cs et l’avoir ajouté à votre projet, affectez la valeur **True** à la propriété **Inscrire pour COM Interop**. Pour plus d’informations, consultez [NIB : Guide pratique pour inscrire un composant pour COM Interop](http://msdn.microsoft.com/en-us/4de7d474-56e8-4027-994d-d47ca4725c5e).  
  
 L’exposition d’objets Visual C# à COM nécessite de déclarer une interface de classe, une interface d’événements si nécessaire, et la classe proprement dite. Les membres de classe doivent suivre ces règles pour être visibles par COM :  
  
-   La classe doit être publique.  
  
-   Les propriétés, méthodes et événements doivent être publics.  
  
-   Les propriétés et méthodes doivent être déclarées dans l’interface de classe.  
  
-   Les événements doivent être déclarés dans l’interface d’événement.  
  
 Les autres membres publics de la classe qui ne sont pas déclarés dans ces interfaces ne seront pas visibles par COM, mais ils seront visibles par d’autres objets .NET Framework.  
  
 Pour exposer des propriétés et des méthodes à COM, vous devez les déclarer sur l’interface de classe, les marquer avec un attribut `DispId` et les implémenter dans la classe. L’ordre dans lequel les membres sont déclarés dans l’interface est l’ordre utilisé pour la vtable COM.  
  
 Pour exposer des événements à partir de votre classe, vous devez les déclarer sur l’interface d’événement et les marquer avec un attribut `DispId`. La classe ne doit pas implémenter cette interface.  
  
 La classe implémente l’interface de classe ; elle peut implémenter plusieurs interfaces, mais la première implémentation sera l’interface de classe par défaut. Implémentez ici les méthodes et propriétés exposées à COM. Elles doivent être marquées comme publiques et doivent correspondre aux déclarations dans l’interface de classe. Vous devez aussi déclarer ici les événements déclenchés par la classe. Ils doivent être marqués comme publics et doivent correspondre aux déclarations dans l’interface d’événement.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Interopérabilité](../../../csharp/programming-guide/interop/index.md)   
 [Page Générer, Concepteur de projet (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)

