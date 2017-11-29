---
title: "Validation de la complexité de mot de passe (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bdbe5f385c6b7a0898c4907b0d8afabdaed06fa0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="9b78f-102">Procédure pas à pas : validation de la complexité des mots de passe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b78f-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="9b78f-103">Cette méthode vérifie certaines caractéristiques du mot de passe fort et met à jour un paramètre de chaîne avec des informations sur les vérifications le mot de passe échoue.</span><span class="sxs-lookup"><span data-stu-id="9b78f-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="9b78f-104">Les mots de passe peuvent être utilisés dans un système sécurisé pour autoriser un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9b78f-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="9b78f-105">Toutefois, les mots de passe doivent être difficiles pour les utilisateurs non autorisés de deviner.</span><span class="sxs-lookup"><span data-stu-id="9b78f-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="9b78f-106">Les intrus peuvent utiliser un *attaque par dictionnaire* programme, qui itère au sein de tous les mots dans un dictionnaire (ou plusieurs dictionnaires dans différentes langues) et teste si les mots comme mot de passe d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9b78f-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="9b78f-107">Mots de passe faibles tels que « Yankees » ou « Mustang » peuvent être devinés rapidement.</span><span class="sxs-lookup"><span data-stu-id="9b78f-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="9b78f-108">Les mots de passe plus forts, tel que « ? Vous «L1N3vaFiNdMeyeP@sSWerd! », sont beaucoup moins susceptibles d’être deviné.</span><span class="sxs-lookup"><span data-stu-id="9b78f-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="9b78f-109">Un système protégé par mot de passe doit s’assurer que les utilisateurs choisissent des mots de passe forts.</span><span class="sxs-lookup"><span data-stu-id="9b78f-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="9b78f-110">Un mot de passe fort est complexe (contenant un mélange de caractères majuscules, minuscules, numériques et spéciaux) et n’est pas un mot.</span><span class="sxs-lookup"><span data-stu-id="9b78f-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="9b78f-111">Cet exemple montre comment vérifier la complexité.</span><span class="sxs-lookup"><span data-stu-id="9b78f-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b78f-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="9b78f-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="9b78f-113">Code</span><span class="sxs-lookup"><span data-stu-id="9b78f-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9b78f-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="9b78f-114">Compiling the Code</span></span>  
 <span data-ttu-id="9b78f-115">Appelez cette méthode en passant la chaîne qui contient ce mot de passe.</span><span class="sxs-lookup"><span data-stu-id="9b78f-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="9b78f-116">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="9b78f-116">This example requires:</span></span>  
  
-   <span data-ttu-id="9b78f-117">Un accès aux membres de l’espace de noms <xref:System.Text.RegularExpressions>.</span><span class="sxs-lookup"><span data-stu-id="9b78f-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="9b78f-118">Ajoutez une instruction `Imports` si vous n’utilisez pas de noms de membres qualifiés complets dans votre code.</span><span class="sxs-lookup"><span data-stu-id="9b78f-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="9b78f-119">Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="9b78f-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="9b78f-120">Sécurité</span><span class="sxs-lookup"><span data-stu-id="9b78f-120">Security</span></span>  
 <span data-ttu-id="9b78f-121">Si vous déplacez le mot de passe sur un réseau, vous devez utiliser une méthode sécurisée pour transférer des données.</span><span class="sxs-lookup"><span data-stu-id="9b78f-121">If you are moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="9b78f-122">Pour plus d’informations, consultez [sécurité des applications Web ASP.NET](https://msdn.microsoft.com/library/330a99hc).</span><span class="sxs-lookup"><span data-stu-id="9b78f-122">For more information, see [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc).</span></span>  
  
 <span data-ttu-id="9b78f-123">Vous pouvez améliorer la précision de la `ValidatePassword` fonction en ajoutant des contrôles de complexité supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="9b78f-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
-   <span data-ttu-id="9b78f-124">Comparez le mot de passe et ses sous-chaînes le nom d’utilisateur, identificateur d’utilisateur et un dictionnaire défini par l’application.</span><span class="sxs-lookup"><span data-stu-id="9b78f-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="9b78f-125">En outre, considérez les caractères visuellement semblables comme équivalents lorsque vous effectuez des comparaisons.</span><span class="sxs-lookup"><span data-stu-id="9b78f-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="9b78f-126">Par exemple, considérez les lettres « l » et « e » comme équivalentes aux chiffres « 1 » et « 3 ».</span><span class="sxs-lookup"><span data-stu-id="9b78f-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
-   <span data-ttu-id="9b78f-127">S’il n'existe qu’un seul caractère en majuscule, assurez-vous qu’il n’est pas premier caractère du mot de passe.</span><span class="sxs-lookup"><span data-stu-id="9b78f-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
-   <span data-ttu-id="9b78f-128">Assurez-vous que les deux derniers caractères du mot de passe sont des caractères alphabétiques.</span><span class="sxs-lookup"><span data-stu-id="9b78f-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
-   <span data-ttu-id="9b78f-129">N’autorisez pas les mots de passe dans lequel tous les symboles sont entrés à partir de la ligne du haut du clavier.</span><span class="sxs-lookup"><span data-stu-id="9b78f-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b78f-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b78f-130">See Also</span></span>  
 <xref:System.Text.RegularExpressions.Regex>  
 [<span data-ttu-id="9b78f-131">Sécurité des applications web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9b78f-131">ASP.NET Web Application Security</span></span>](https://msdn.microsoft.com/library/330a99hc)
