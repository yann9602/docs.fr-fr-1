---
title: "Liaison anticipée et liaison tardive (Visual Basic)"
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
- early binding
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding, Visual Basic compiler
- binding, late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding
- late binding, Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
caps.latest.revision: 10
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 66a34580417fb8b4a814b237ec36ffe700b1b30a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="202cd-102">Liaison anticipée et liaison tardive (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="202cd-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="202cd-103">Le compilateur [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] exécute un processus appelé `binding` lorsqu’un objet est affecté à une variable objet.</span><span class="sxs-lookup"><span data-stu-id="202cd-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="202cd-104">Un objet est dit *à liaison anticipée* lorsqu’il est affecté à une variable déclarée comme étant d’un type d’objet spécifique.</span><span class="sxs-lookup"><span data-stu-id="202cd-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="202cd-105">Les objets à liaison anticipée permettent au compilateur d’allouer de la mémoire et d’effectuer d’autres optimisations avant l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="202cd-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="202cd-106">Par exemple, le fragment de code suivant déclare une variable de type <xref:System.IO.FileStream> :</span><span class="sxs-lookup"><span data-stu-id="202cd-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 <span data-ttu-id="202cd-107">[!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="202cd-107">[!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_1.vb)]</span></span>  
  
 <span data-ttu-id="202cd-108">Étant donné que <xref:System.IO.FileStream> est un type d’objet spécifique, l’instance affectée à `FS` est à liaison anticipée.</span><span class="sxs-lookup"><span data-stu-id="202cd-108">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="202cd-109">Par opposition, un objet est dit *à liaison tardive* lorsqu’il est affecté à une variable déclarée comme étant du type `Object`.</span><span class="sxs-lookup"><span data-stu-id="202cd-109">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="202cd-110">Les objets de ce type peuvent contenir des références à n’importe quel objet, mais ne présentent pas tous les avantages des objets à liaison anticipée.</span><span class="sxs-lookup"><span data-stu-id="202cd-110">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="202cd-111">Par exemple, le fragment de code suivant déclare une variable objet qui contient un objet retourné par la fonction `CreateObject` :</span><span class="sxs-lookup"><span data-stu-id="202cd-111">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 <span data-ttu-id="202cd-112">[!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="202cd-112">[!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_2.vb)]</span></span>  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="202cd-113">Avantages de la liaison anticipée</span><span class="sxs-lookup"><span data-stu-id="202cd-113">Advantages of Early Binding</span></span>  
 <span data-ttu-id="202cd-114">Utilisez des objets à liaison anticipée chaque fois que c’est possible, car ils permettent au compilateur d’effectuer d’importantes optimisations qui génèrent des applications plus efficaces.</span><span class="sxs-lookup"><span data-stu-id="202cd-114">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="202cd-115">Les objets à liaison anticipée sont considérablement plus rapides que les objets à liaison tardive et rendent votre code plus facile à lire et à gérer en indiquant exactement quels types d’objets sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="202cd-115">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="202cd-116">La liaison anticipée présente également l’avantage d’offrir des fonctions utiles, comme la saisie semi-automatique de code et l’aide dynamique, car l’environnement de développement intégré (IDE) [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] peut déterminer avec précision le type d’objet utilisé lorsque vous modifiez le code.</span><span class="sxs-lookup"><span data-stu-id="202cd-116">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="202cd-117">Elle réduit le nombre et la gravité des erreurs d’exécution, car elle permet au compilateur de signaler des erreurs à la compilation du programme.</span><span class="sxs-lookup"><span data-stu-id="202cd-117">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="202cd-118">La liaison tardive ne peut être utilisée que pour accéder aux membres de type déclarés comme `Public`.</span><span class="sxs-lookup"><span data-stu-id="202cd-118">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="202cd-119">L’accès aux membres déclarés comme `Friend` ou `Protected Friend` provoque une erreur d’exécution.</span><span class="sxs-lookup"><span data-stu-id="202cd-119">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="202cd-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="202cd-120">See Also</span></span>  
 <span data-ttu-id="202cd-121"><xref:Microsoft.VisualBasic.Interaction.CreateObject%2A></span><span class="sxs-lookup"><span data-stu-id="202cd-121"><xref:Microsoft.VisualBasic.Interaction.CreateObject%2A></span></span>   
 <span data-ttu-id="202cd-122">[Durée de vie d’un objet : création et destruction des objets](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md) </span><span class="sxs-lookup"><span data-stu-id="202cd-122">[Object Lifetime: How Objects Are Created and Destroyed](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md) </span></span>  
 [<span data-ttu-id="202cd-123">Object (type de données)</span><span class="sxs-lookup"><span data-stu-id="202cd-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)

