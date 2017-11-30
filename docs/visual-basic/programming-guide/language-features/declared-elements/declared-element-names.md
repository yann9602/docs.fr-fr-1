---
title: "Noms d'éléments déclarés (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 691b65280b958edcf8e856ee6df793e0b7b05184
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="e0963-102">Noms d'éléments déclarés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0963-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="e0963-103">Chaque élément déclaré a un nom, également appelé un *identificateur*, qui est utilisé par le code qui y fait référence.</span><span class="sxs-lookup"><span data-stu-id="e0963-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="e0963-104">Règles</span><span class="sxs-lookup"><span data-stu-id="e0963-104">Rules</span></span>  
 <span data-ttu-id="e0963-105">Un nom d’élément dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] doit respecter les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="e0963-105">An element name in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must observe the following rules:</span></span>  
  
-   <span data-ttu-id="e0963-106">Il doit commencer par un caractère alphabétique ou un trait de soulignement (`_`).</span><span class="sxs-lookup"><span data-stu-id="e0963-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="e0963-107">Il doit contenir uniquement des caractères alphabétiques, des chiffres décimaux et des traits de soulignement.</span><span class="sxs-lookup"><span data-stu-id="e0963-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
-   <span data-ttu-id="e0963-108">Il doit contenir au moins un caractère alphabétique ou un chiffre décimal s’il commence par un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="e0963-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
-   <span data-ttu-id="e0963-109">Il ne doit pas être plus de 1023 caractères.</span><span class="sxs-lookup"><span data-stu-id="e0963-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="e0963-110">La longueur maximale de 1023 caractères s’applique également à la chaîne entière d’un nom qualifié complet, tel que `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span><span class="sxs-lookup"><span data-stu-id="e0963-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="e0963-111">L’exemple suivant illustre certains noms d’élément valide.</span><span class="sxs-lookup"><span data-stu-id="e0963-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="e0963-112">L’exemple suivant illustre certains noms d’élément non valide.</span><span class="sxs-lookup"><span data-stu-id="e0963-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="e0963-113">Le premier contient uniquement un trait de soulignement, le second commence par un chiffre décimal et le troisième contient un caractère non valide ($).</span><span class="sxs-lookup"><span data-stu-id="e0963-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  <span data-ttu-id="e0963-114">Les noms d’élément commençant par un trait de soulignement (`_`) ne font pas partie de la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS), le code conforme CLS ne peut pas utiliser un composant qui définit les noms de ce type.</span><span class="sxs-lookup"><span data-stu-id="e0963-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="e0963-115">Toutefois, un trait de soulignement dans n’importe quelle autre position dans un nom d’élément est conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="e0963-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="e0963-116">Instructions de longueur de nom</span><span class="sxs-lookup"><span data-stu-id="e0963-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="e0963-117">Un point de vue pratique, votre nom doit être aussi court que possible tout en identifiant clairement la nature de l’élément.</span><span class="sxs-lookup"><span data-stu-id="e0963-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="e0963-118">Cela améliore la lisibilité de votre code et réduit la taille du fichier source et de longueur de ligne.</span><span class="sxs-lookup"><span data-stu-id="e0963-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="e0963-119">En revanche, votre nom ne doit pas être court que ne pas correctement décrit ce que représente l’élément et la façon dont votre code utilise.</span><span class="sxs-lookup"><span data-stu-id="e0963-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="e0963-120">Ceci est important pour la lisibilité de votre code.</span><span class="sxs-lookup"><span data-stu-id="e0963-120">This is important for the readability of your code.</span></span> <span data-ttu-id="e0963-121">Si quelqu'un d’autre tente de le comprendre, ou si vous devez l’observer longtemps après que l’avoir écrit, noms d’éléments appropriés peuvent enregistrer un temps considérable.</span><span class="sxs-lookup"><span data-stu-id="e0963-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="e0963-122">Noms d’échappement</span><span class="sxs-lookup"><span data-stu-id="e0963-122">Escaped Names</span></span>  
 <span data-ttu-id="e0963-123">En règle générale, un nom d’élément ne doit pas correspondre à un des mots clés réservés par [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], tel que `Case` ou `Friend`.</span><span class="sxs-lookup"><span data-stu-id="e0963-123">Generally, an element name must not match any of the keywords reserved by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], such as `Case` or `Friend`.</span></span> <span data-ttu-id="e0963-124">Toutefois, vous pouvez définir un *nom échappement*, lequel est placé entre crochets (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="e0963-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="e0963-125">Un nom d’échappement peut correspondre à tout [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] (mot clé), étant donné que les crochets supprimer toute ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="e0963-125">An escaped name can match any [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="e0963-126">Vous utilisez également les crochets lorsque vous faites référence au nom ultérieurement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="e0963-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="e0963-127">En règle générale, vous devez utiliser des noms échappés uniquement lorsque :</span><span class="sxs-lookup"><span data-stu-id="e0963-127">In general, you should use escaped names only when:</span></span>  
  
-   <span data-ttu-id="e0963-128">Votre code a migré à partir d’une version antérieure de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] qui n’a pas réservé le mot clé utilisé comme un nom ; ou</span><span class="sxs-lookup"><span data-stu-id="e0963-128">Your code has migrated from a previous version of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] that did not reserve the keyword being used as a name; or</span></span>  
  
-   <span data-ttu-id="e0963-129">Vous travaillez avec du code écrit dans un autre langage dans lequel le mot clé donné n’est pas réservé.</span><span class="sxs-lookup"><span data-stu-id="e0963-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="e0963-130">Dans le cas contraire, vous devez envisager de renommer l’élément si son nom est en conflit avec un mot clé.</span><span class="sxs-lookup"><span data-stu-id="e0963-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="e0963-131">L’environnement de développement intégré (IDE) fournit un moyen simple pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="e0963-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="e0963-132">Pour plus d’informations, consultez [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span><span class="sxs-lookup"><span data-stu-id="e0963-132">For more information, see [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="e0963-133">Respect de la casse dans les noms</span><span class="sxs-lookup"><span data-stu-id="e0963-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="e0963-134">Noms d’élément dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="e0963-134">Element names in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] are case-insensitive.</span></span> <span data-ttu-id="e0963-135">Cela signifie que lorsque le compilateur compare deux noms qui diffèrent uniquement par la casse des lettres, il les interprète comme étant le même nom.</span><span class="sxs-lookup"><span data-stu-id="e0963-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="e0963-136">Par exemple, il considère que `ABC` et `abc` font référence au même élément déclaré.</span><span class="sxs-lookup"><span data-stu-id="e0963-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="e0963-137">Toutefois, le common language runtime (CLR) utilise une liaison qui respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="e0963-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="e0963-138">Ainsi, quand vous générez un assembly ou une DLL et que vous le mettez à disposition d’autres assemblys, la casse de vos noms est respectée.</span><span class="sxs-lookup"><span data-stu-id="e0963-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="e0963-139">Par exemple, si vous définissez une classe avec un élément nommé `ABC`et que d’autres assemblys utilisent votre classe par le biais du Common Language Runtime, ils doivent faire référence à l’élément en tant que `ABC`.</span><span class="sxs-lookup"><span data-stu-id="e0963-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="e0963-140">Si vous recompilez votre classe par la suite et modifier le nom de l’élément à `abc`, les autres assemblys utilisent votre classe pourraient ne plus accéder à cet élément.</span><span class="sxs-lookup"><span data-stu-id="e0963-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="e0963-141">Ainsi, quand vous publiez une version mise à jour d’un assembly, vous ne devez pas modifier la casse des éléments publics.</span><span class="sxs-lookup"><span data-stu-id="e0963-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="e0963-142">Les noms et les paramètres régionaux</span><span class="sxs-lookup"><span data-stu-id="e0963-142">Names and Locales</span></span>  
 <span data-ttu-id="e0963-143">Comparaison des noms est indépendante des paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="e0963-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="e0963-144">Si deux noms correspondent dans des paramètres régionaux, ils sont garanties à faire correspondre dans tous les paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="e0963-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0963-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0963-145">See Also</span></span>  
 [<span data-ttu-id="e0963-146">Éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="e0963-146">Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [<span data-ttu-id="e0963-147">Caractéristiques d’éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="e0963-147">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="e0963-148">Références aux éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="e0963-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="e0963-149">Instructions</span><span class="sxs-lookup"><span data-stu-id="e0963-149">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
