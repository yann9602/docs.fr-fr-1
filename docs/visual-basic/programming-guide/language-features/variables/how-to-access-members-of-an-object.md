---
title: "Comment : accéder aux membres d'un objet (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 85fa4932b449bf7b9ecb3902fc17fd954ea8cfac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="42012-102">Comment : accéder aux membres d'un objet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42012-102">How to: Access Members of an Object (Visual Basic)</span></span>
<span data-ttu-id="42012-103">Lorsque vous disposez d’une variable objet qui fait référence à un objet, vous souhaitez souvent travailler avec les membres de cet objet, comme ses méthodes, propriétés, champs et des événements.</span><span class="sxs-lookup"><span data-stu-id="42012-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="42012-104">Par exemple, après avoir créé un nouveau <xref:System.Windows.Forms.Form> de l’objet, vous souhaiterez peut-être définir son <xref:System.Windows.Forms.Control.Text%2A> propriété ou l’appel de ses <xref:System.Windows.Forms.Control.Focus%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="42012-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>  
  
## <a name="accessing-members"></a><span data-ttu-id="42012-105">L’accès aux membres</span><span class="sxs-lookup"><span data-stu-id="42012-105">Accessing Members</span></span>  
 <span data-ttu-id="42012-106">Vous accéder aux membres d’un objet via la variable qui fait référence à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="42012-106">You access an object's members through the variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="42012-107">Pour accéder aux membres d’un objet</span><span class="sxs-lookup"><span data-stu-id="42012-107">To access members of an object</span></span>  
  
-   <span data-ttu-id="42012-108">Utilisez l’opérateur d’accès aux membres (`.`) entre le nom de variable objet et le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="42012-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     <span data-ttu-id="42012-109">Si le membre est [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), vous n’avez pas besoin d’une variable pour y accéder.</span><span class="sxs-lookup"><span data-stu-id="42012-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>  
  
## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="42012-110">L’accès aux membres d’un objet de Type connu</span><span class="sxs-lookup"><span data-stu-id="42012-110">Accessing Members of an Object of Known Type</span></span>  
 <span data-ttu-id="42012-111">Si vous connaissez le type d’un objet au moment de la compilation, vous pouvez utiliser *liaison anticipée* pour une variable qui fait référence à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="42012-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="42012-112">Pour accéder aux membres d’un objet dont vous connaissez le type au moment de la compilation</span><span class="sxs-lookup"><span data-stu-id="42012-112">To access members of an object for which you know the type at compile time</span></span>  
  
1.  <span data-ttu-id="42012-113">Déclarez la variable objet comme étant du type de l’objet que vous prévoyez d’affecter à la variable.</span><span class="sxs-lookup"><span data-stu-id="42012-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     <span data-ttu-id="42012-114">Avec `Option Strict On`, vous pouvez affecter uniquement <xref:System.Windows.Forms.Form> objets (ou objets d’un type dérivé <xref:System.Windows.Forms.Form>) à `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="42012-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="42012-115">Si vous avez défini une classe ou une structure avec une étendue `CType` conversion <xref:System.Windows.Forms.Form>, vous pouvez également affecter cette classe ou structure `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="42012-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>  
  
2.  <span data-ttu-id="42012-116">Utilisez l’opérateur d’accès aux membres (`.`) entre le nom de variable objet et le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="42012-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    extraForm.Show()  
    ```  
  
     <span data-ttu-id="42012-117">Vous pouvez accéder à toutes les méthodes et propriétés spécifiques à la <xref:System.Windows.Forms.Form> (classe), quel que soit ce que le `Option Strict` paramètre est.</span><span class="sxs-lookup"><span data-stu-id="42012-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="42012-118">L’accès aux membres d’un objet de Type inconnu</span><span class="sxs-lookup"><span data-stu-id="42012-118">Accessing Members of an Object of Unknown Type</span></span>  
 <span data-ttu-id="42012-119">Si vous ne connaissez pas le type d’un objet au moment de la compilation, vous devez utiliser *liaison tardive* pour n’importe quelle variable qui fait référence à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="42012-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="42012-120">Pour accéder aux membres d’un objet pour lequel vous ignorez le type au moment de la compilation</span><span class="sxs-lookup"><span data-stu-id="42012-120">To access members of an object for which you do not know the type at compile time</span></span>  
  
1.  <span data-ttu-id="42012-121">Déclarez la variable objet de la [Type de données d’objet](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="42012-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="42012-122">(Déclaration d’une variable en tant que `Object` est identique à la déclarer comme <xref:System.Object?displayProperty=nameWithType>.)</span><span class="sxs-lookup"><span data-stu-id="42012-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>  
  
    ```  
    Dim someControl As Object  
    ```  
  
     <span data-ttu-id="42012-123">Avec `Option Strict On`, vous pouvez accéder uniquement aux membres qui sont définis sur la <xref:System.Object> classe.</span><span class="sxs-lookup"><span data-stu-id="42012-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>  
  
2.  <span data-ttu-id="42012-124">Utilisez l’opérateur d’accès aux membres (`.`) entre le nom de variable objet et le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="42012-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    someControl.GetType()  
    ```  
  
     <span data-ttu-id="42012-125">Pour pouvoir accéder aux membres de n’importe quel objet que vous assignez à la variable objet, vous devez définir `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="42012-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="42012-126">Dans ce cas, le compilateur ne peut pas garantir qu’un membre donné est exposé par l’objet que vous affectez à la variable.</span><span class="sxs-lookup"><span data-stu-id="42012-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="42012-127">Si l’objet n’expose pas un membre de tenter d’y accéder, un <xref:System.MemberAccessException> cette exception est levée.</span><span class="sxs-lookup"><span data-stu-id="42012-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42012-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42012-128">See Also</span></span>  
 <xref:System.Object>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.MemberAccessException>  
 [<span data-ttu-id="42012-129">Variables objets</span><span class="sxs-lookup"><span data-stu-id="42012-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="42012-130">Déclaration des variables objets</span><span class="sxs-lookup"><span data-stu-id="42012-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="42012-131">Object (type de données)</span><span class="sxs-lookup"><span data-stu-id="42012-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="42012-132">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="42012-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
