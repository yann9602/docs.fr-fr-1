---
title: "Comment : créer une propriété (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d140e6a10061f7fabe3d12c6cce5d0c201e103d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-property-visual-basic"></a><span data-ttu-id="cbe90-102">Comment : créer une propriété (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbe90-102">How to: Create a Property (Visual Basic)</span></span>
<span data-ttu-id="cbe90-103">Vous placez une définition de propriété entre un `Property` instruction et un `End Property` instruction.</span><span class="sxs-lookup"><span data-stu-id="cbe90-103">You enclose a property definition between a `Property` statement and an `End Property` statement.</span></span> <span data-ttu-id="cbe90-104">Dans cette définition, définissez une `Get` procédure, un `Set` procédure, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="cbe90-104">Within this definition you define a `Get` procedure, a `Set` procedure, or both.</span></span> <span data-ttu-id="cbe90-105">Code de toutes les propriétés se trouve dans ces procédures.</span><span class="sxs-lookup"><span data-stu-id="cbe90-105">All the property's code lies within these procedures.</span></span>  
  
 <span data-ttu-id="cbe90-106">Le `Get` procédure récupère la valeur de propriété et la `Set` stocke une valeur.</span><span class="sxs-lookup"><span data-stu-id="cbe90-106">The `Get` procedure retrieves the property's value, and the `Set` procedure stores a value.</span></span> <span data-ttu-id="cbe90-107">Si vous souhaitez que la propriété à accéder en lecture/écriture, vous devez définir les deux procédures.</span><span class="sxs-lookup"><span data-stu-id="cbe90-107">If you want the property to have read/write access, you must define both procedures.</span></span> <span data-ttu-id="cbe90-108">Pour une propriété en lecture seule, vous définissez uniquement `Get`, et pour une propriété en écriture seule, vous définissez uniquement `Set`.</span><span class="sxs-lookup"><span data-stu-id="cbe90-108">For a read-only property, you define only `Get`, and for a write-only property, you define only `Set`.</span></span>  
  
### <a name="to-create-a-property"></a><span data-ttu-id="cbe90-109">Pour créer une propriété</span><span class="sxs-lookup"><span data-stu-id="cbe90-109">To create a property</span></span>  
  
1.  <span data-ttu-id="cbe90-110">En dehors d’une propriété ou une procédure, utilisez un [Property, instruction](../../../../visual-basic/language-reference/statements/property-statement.md), suivi d’un `End Property` instruction.</span><span class="sxs-lookup"><span data-stu-id="cbe90-110">Outside any property or procedure, use a [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md), followed by an `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="cbe90-111">Si la propriété accepte des paramètres, suivez le `Property` mot clé avec le nom de la procédure, puis la liste de paramètres entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="cbe90-111">If the property takes parameters, follow the `Property` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="cbe90-112">Suivez les parenthèses d’une `As` clause pour spécifier le type de données de la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="cbe90-112">Follow the parentheses with an `As` clause to specify the data type of the property's value.</span></span> <span data-ttu-id="cbe90-113">Vous devez spécifier le type de données, même pour une propriété en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="cbe90-113">You must specify the data type even for a write-only property.</span></span>  
  
4.  <span data-ttu-id="cbe90-114">Ajouter `Get` et `Set` procédures, comme il convient.</span><span class="sxs-lookup"><span data-stu-id="cbe90-114">Add `Get` and `Set` procedures, as appropriate.</span></span> <span data-ttu-id="cbe90-115">Reportez-vous aux instructions suivantes.</span><span class="sxs-lookup"><span data-stu-id="cbe90-115">See the following directions.</span></span>  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a><span data-ttu-id="cbe90-116">Pour créer une procédure Get qui Récupère une valeur de propriété</span><span class="sxs-lookup"><span data-stu-id="cbe90-116">To create a Get procedure that retrieves a property value</span></span>  
  
1.  <span data-ttu-id="cbe90-117">Entre le `Property` et `End Property` écrire des instructions, une [instruction Get](../../../../visual-basic/language-reference/statements/get-statement.md), suivi d’un `End Get` instruction.</span><span class="sxs-lookup"><span data-stu-id="cbe90-117">Between the `Property` and `End Property` statements, write a [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md), followed by an `End Get` statement.</span></span> <span data-ttu-id="cbe90-118">Vous n’avez pas besoin définir des paramètres pour le `Get` procédure.</span><span class="sxs-lookup"><span data-stu-id="cbe90-118">You do not need to define any parameters for the `Get` procedure.</span></span>  
  
2.  <span data-ttu-id="cbe90-119">Placez les instructions de code pour récupérer la valeur de propriété entre le `Get` et `End Get` instructions.</span><span class="sxs-lookup"><span data-stu-id="cbe90-119">Place the code statements to retrieve the property's value between the `Get` and `End Get` statements.</span></span> <span data-ttu-id="cbe90-120">Ce code peut inclure les autres calculs et des manipulations de données en plus de la génération et du retour de la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="cbe90-120">This code can include other calculations and data manipulations in addition to generating and returning the property's value.</span></span>  
  
3.  <span data-ttu-id="cbe90-121">Utilisez un `Return` instruction pour retourner la valeur de propriété au code appelant.</span><span class="sxs-lookup"><span data-stu-id="cbe90-121">Use a `Return` statement to return the property's value to the calling code.</span></span>  
  
 <span data-ttu-id="cbe90-122">Vous devez écrire un `Get` procédure pour une propriété en lecture-écriture et pour une propriété en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="cbe90-122">You must write a `Get` procedure for a read-write property and for a read-only property.</span></span> <span data-ttu-id="cbe90-123">Vous ne devez pas définir un `Get` procédure pour une propriété en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="cbe90-123">You must not define a `Get` procedure for a write-only property.</span></span>  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a><span data-ttu-id="cbe90-124">Pour créer une procédure Set qui écrit une valeur de propriété</span><span class="sxs-lookup"><span data-stu-id="cbe90-124">To create a Set procedure that writes a property's value</span></span>  
  
1.  <span data-ttu-id="cbe90-125">Entre le `Property` et `End Property` écrire des instructions, une [instruction Set](../../../../visual-basic/language-reference/statements/set-statement.md), suivi d’un `End Set` instruction.</span><span class="sxs-lookup"><span data-stu-id="cbe90-125">Between the `Property` and `End Property` statements, write a [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md), followed by an `End Set` statement.</span></span>  
  
2.  <span data-ttu-id="cbe90-126">Dans le `Set` instruction, suivez le `Set` mot clé avec une liste de paramètres entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="cbe90-126">In the `Set` statement, follow the `Set` keyword with a parameter list in parentheses.</span></span> <span data-ttu-id="cbe90-127">Cette liste de paramètres doit inclure au moins un paramètre de valeur pour la valeur passée par le code appelant.</span><span class="sxs-lookup"><span data-stu-id="cbe90-127">This parameter list must include at least a value parameter for the value passed by the calling code.</span></span> <span data-ttu-id="cbe90-128">Le nom par défaut pour ce paramètre de valeur est `Value`, mais vous pouvez utiliser un nom différent si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="cbe90-128">The default name for this value parameter is `Value`, but you can use a different name if appropriate.</span></span> <span data-ttu-id="cbe90-129">Le paramètre de valeur doit avoir les mêmes type de données en tant que la propriété proprement dite.</span><span class="sxs-lookup"><span data-stu-id="cbe90-129">The value parameter must have the same data type as the property itself.</span></span>  
  
3.  <span data-ttu-id="cbe90-130">Placez les instructions de code pour stocker une valeur dans la propriété entre les `Set` et `End Set` instructions.</span><span class="sxs-lookup"><span data-stu-id="cbe90-130">Place the code statements to store a value in the property between the `Set` and `End Set` statements.</span></span> <span data-ttu-id="cbe90-131">Ce code peut inclure les autres calculs et des manipulations de données en plus de la validation et le stockage de la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="cbe90-131">This code can include other calculations and data manipulations in addition to validating and storing the property's value.</span></span>  
  
4.  <span data-ttu-id="cbe90-132">Utilisez le paramètre value pour accepter la valeur fournie par le code appelant.</span><span class="sxs-lookup"><span data-stu-id="cbe90-132">Use the value parameter to accept the value supplied by the calling code.</span></span> <span data-ttu-id="cbe90-133">Vous pouvez stocker cette valeur directement dans une instruction d’assignation ou utiliser dans une expression pour calculer la valeur interne à stocker.</span><span class="sxs-lookup"><span data-stu-id="cbe90-133">You can either store this value directly in an assignment statement, or use it in an expression to calculate the internal value to be stored.</span></span>  
  
 <span data-ttu-id="cbe90-134">Vous devez écrire un `Set` procédure pour une propriété en lecture-écriture et pour une propriété en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="cbe90-134">You must write a `Set` procedure for a read-write property and for a write-only property.</span></span> <span data-ttu-id="cbe90-135">Vous ne devez pas définir un `Set` procédure pour une propriété en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="cbe90-135">You must not define a `Set` procedure for a read-only property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbe90-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="cbe90-136">Example</span></span>  
 <span data-ttu-id="cbe90-137">L’exemple suivant crée une propriété en lecture/écriture qui stocke un nom complet comme deux noms constitutifs, le prénom et le nom de famille.</span><span class="sxs-lookup"><span data-stu-id="cbe90-137">The following example creates a read/write property that stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="cbe90-138">Lorsque le code appelant lit `fullName`, le `Get` procédure combine les deux noms constitutifs et retourne le nom complet.</span><span class="sxs-lookup"><span data-stu-id="cbe90-138">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="cbe90-139">Lorsque le code appelant assigne un nouveau nom complet, le `Set` procédure tente de diviser en deux noms constitutifs.</span><span class="sxs-lookup"><span data-stu-id="cbe90-139">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="cbe90-140">S’il ne trouve pas d’un espace, il les stocke tout comme le prénom.</span><span class="sxs-lookup"><span data-stu-id="cbe90-140">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/how-to-create-a-property_1.vb)]  
  
 <span data-ttu-id="cbe90-141">L’exemple suivant montre des appels typiques aux procédures de propriété `fullName`.</span><span class="sxs-lookup"><span data-stu-id="cbe90-141">The following example shows typical calls to the property procedures of `fullName`.</span></span> <span data-ttu-id="cbe90-142">Le premier appel définit la valeur de propriété, le deuxième appel récupère.</span><span class="sxs-lookup"><span data-stu-id="cbe90-142">The first call sets the property value and the second call retrieves it.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/how-to-create-a-property_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cbe90-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbe90-143">See Also</span></span>  
 [<span data-ttu-id="cbe90-144">Procédures</span><span class="sxs-lookup"><span data-stu-id="cbe90-144">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="cbe90-145">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="cbe90-145">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="cbe90-146">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="cbe90-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="cbe90-147">Différences entre les propriétés et les Variables en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cbe90-147">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="cbe90-148">Guide pratique : déclarer une propriété avec des niveaux d’accès mixtes</span><span class="sxs-lookup"><span data-stu-id="cbe90-148">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="cbe90-149">Guide pratique : appeler une procédure de propriété</span><span class="sxs-lookup"><span data-stu-id="cbe90-149">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="cbe90-150">Comment : déclarer et appeler une propriété par défaut en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cbe90-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="cbe90-151">Guide pratique : placer une valeur dans une propriété</span><span class="sxs-lookup"><span data-stu-id="cbe90-151">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="cbe90-152">Guide pratique : obtenir une valeur d’une propriété</span><span class="sxs-lookup"><span data-stu-id="cbe90-152">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
