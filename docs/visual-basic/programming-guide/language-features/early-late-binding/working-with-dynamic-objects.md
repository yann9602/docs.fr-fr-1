---
title: "Utilisation d’objets dynamiques (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d1e1c4f7338daad0f1101f6e886eba6c37316b0e
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="working-with-dynamic-objects-visual-basic"></a><span data-ttu-id="95439-102">Utilisation d'objets dynamiques (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95439-102">Working with Dynamic Objects (Visual Basic)</span></span>
<span data-ttu-id="95439-103">Objets dynamiques fournissent une autre manière, autre que le `Object` type, à liaison tardive à un objet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="95439-103">Dynamic objects provide another way, other than the `Object` type, to late bind to an object at run time.</span></span> <span data-ttu-id="95439-104">Un objet dynamique expose des membres tels que les propriétés et les méthodes au moment de l’exécution à l’aide des interfaces dynamiques définies dans le <xref:System.Dynamic>espace de noms.</xref:System.Dynamic></span><span class="sxs-lookup"><span data-stu-id="95439-104">A dynamic object exposes members such as properties and methods at run time by using dynamic interfaces that are defined in the <xref:System.Dynamic> namespace.</span></span> <span data-ttu-id="95439-105">Vous pouvez utiliser les classes dans le <xref:System.Dynamic>espace de noms pour créer des objets qui fonctionnent avec des structures de données qui ne correspondent pas à un format ou le type statique.</xref:System.Dynamic></span><span class="sxs-lookup"><span data-stu-id="95439-105">You can use the classes in the <xref:System.Dynamic> namespace to create objects that work with data structures that do not match a static type or format.</span></span> <span data-ttu-id="95439-106">Vous pouvez également utiliser les objets dynamiques qui sont définies dans les langages dynamiques tels que IronPython et IronRuby.</span><span class="sxs-lookup"><span data-stu-id="95439-106">You can also use the dynamic objects that are defined in dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="95439-107">Pour obtenir des exemples qui montrent comment créer des objets dynamiques ou utiliser un objet dynamique défini dans un langage dynamique, consultez la page [procédure pas à pas : création et l’utilisation d’objets dynamiques](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, ou <xref:System.Dynamic.ExpandoObject>.</xref:System.Dynamic.ExpandoObject> </xref:System.Dynamic.DynamicObject></span><span class="sxs-lookup"><span data-stu-id="95439-107">For examples that show how to create dynamic objects or use a dynamic object defined in a dynamic language, see [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, or <xref:System.Dynamic.ExpandoObject>.</span></span>  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="95439-108">Crée une liaison aux objets des langages dynamiques tels que IronPython et IronRuby et le dynamic language runtime à l’aide de la <xref:System.Dynamic.IDynamicMetaObjectProvider>interface.</xref:System.Dynamic.IDynamicMetaObjectProvider></span><span class="sxs-lookup"><span data-stu-id="95439-108"> binds to objects from the dynamic language runtime and dynamic languages such as IronPython and IronRuby by using the <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span></span> <span data-ttu-id="95439-109">Exemples de classes qui implémentent la `IDynamicMetaObjectProvider` interface sont les <xref:System.Dynamic.DynamicObject>et <xref:System.Dynamic.ExpandoObject>classes.</xref:System.Dynamic.ExpandoObject> </xref:System.Dynamic.DynamicObject></span><span class="sxs-lookup"><span data-stu-id="95439-109">Examples of classes that implement the `IDynamicMetaObjectProvider` interface are the <xref:System.Dynamic.DynamicObject> and <xref:System.Dynamic.ExpandoObject> classes.</span></span>  
  
 <span data-ttu-id="95439-110">Si un appel à liaison tardive est effectué vers un objet qui implémente le `IDynamicMetaObjectProvider` interface, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] lie à l’objet dynamique à l’aide de cette interface.</span><span class="sxs-lookup"><span data-stu-id="95439-110">If a late-bound call is made to an object that implements the `IDynamicMetaObjectProvider` interface, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] binds to the dynamic object by using that interface.</span></span> <span data-ttu-id="95439-111">Si un appel à liaison tardive est effectué vers un objet qui n’implémente pas le `IDynamicMetaObjectProvider` interface, ou si l’appel à la `IDynamicMetaObjectProvider` échoue, l’interface [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] lie à l’objet en utilisant les fonctionnalités de liaison tardive de la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] runtime.</span><span class="sxs-lookup"><span data-stu-id="95439-111">If a late-bound call is made to an object that does not implement the `IDynamicMetaObjectProvider` interface, or if the call to the `IDynamicMetaObjectProvider` interface fails, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] binds to the object by using the late-binding capabilities of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95439-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95439-112">See Also</span></span>  
 <span data-ttu-id="95439-113"><xref:System.Dynamic.DynamicObject></xref:System.Dynamic.DynamicObject></span><span class="sxs-lookup"><span data-stu-id="95439-113"><xref:System.Dynamic.DynamicObject></span></span>   
 <span data-ttu-id="95439-114"><xref:System.Dynamic.ExpandoObject></xref:System.Dynamic.ExpandoObject></span><span class="sxs-lookup"><span data-stu-id="95439-114"><xref:System.Dynamic.ExpandoObject></span></span>   
<span data-ttu-id="95439-115"> [Procédure pas à pas : Création et utilisation d’objets dynamiques](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md) </span><span class="sxs-lookup"><span data-stu-id="95439-115"> [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md) </span></span>  
<span data-ttu-id="95439-116"> [Liaison anticipée et liaison tardive](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)</span><span class="sxs-lookup"><span data-stu-id="95439-116"> [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)</span></span>
