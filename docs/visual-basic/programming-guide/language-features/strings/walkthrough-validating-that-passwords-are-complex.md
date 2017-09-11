---
title: "Validation de complexité des mots de passe (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- String data type, validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: 17
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
ms.openlocfilehash: 8d636c1e43de6a108cdc217cb21aaf7689e175f7
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="f2877-102">Procédure pas à pas : validation de la complexité des mots de passe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2877-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="f2877-103">Cette méthode vérifie certaines caractéristiques de mot de passe fort et met à jour un paramètre de chaîne avec les informations sur les vérifications le mot de passe échoue.</span><span class="sxs-lookup"><span data-stu-id="f2877-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="f2877-104">Les mots de passe peuvent être utilisés dans un système sécurisé pour autoriser un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f2877-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="f2877-105">Toutefois, les mots de passe doivent être difficiles pour les utilisateurs non autorisés de deviner.</span><span class="sxs-lookup"><span data-stu-id="f2877-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="f2877-106">Les intrus peuvent utiliser un *attaque par dictionnaire* programme, qui effectue une itération dans tous les mots dans un dictionnaire (ou plusieurs dictionnaires dans différentes langues) et teste si les mots comme mot de passe d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f2877-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="f2877-107">Mots de passe faibles tels que « Yankees » ou « Mustang » peuvent être devinés rapidement.</span><span class="sxs-lookup"><span data-stu-id="f2877-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="f2877-108">Les mots de passe plus forts, tel que « ? Vous «L1N3vaFiNdMeyeP@sSWerd! », sont beaucoup moins susceptibles d’être découvert.</span><span class="sxs-lookup"><span data-stu-id="f2877-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="f2877-109">Un système protégé par mot de passe doit s’assurer que les utilisateurs choisissent des mots de passe forts.</span><span class="sxs-lookup"><span data-stu-id="f2877-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="f2877-110">Un mot de passe fort est complexe (contenant un mélange de caractères majuscules, minuscules, numériques et spéciaux) et n’est pas un mot.</span><span class="sxs-lookup"><span data-stu-id="f2877-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="f2877-111">Cet exemple montre comment vérifier la complexité.</span><span class="sxs-lookup"><span data-stu-id="f2877-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2877-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="f2877-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="f2877-113">Code</span><span class="sxs-lookup"><span data-stu-id="f2877-113">Code</span></span>  
 <span data-ttu-id="f2877-114">[!code-vb[VbVbcnRegEx n °&1;](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f2877-114">[!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f2877-115">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f2877-115">Compiling the Code</span></span>  
 <span data-ttu-id="f2877-116">Appelez cette méthode en passant la chaîne qui contient le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f2877-116">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="f2877-117">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="f2877-117">This example requires:</span></span>  
  
-   <span data-ttu-id="f2877-118">Accès aux membres de la <xref:System.Text.RegularExpressions>espace de noms.</xref:System.Text.RegularExpressions></span><span class="sxs-lookup"><span data-stu-id="f2877-118">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="f2877-119">Ajouter un `Imports` instruction si vous n’utilisez pas des noms de membres qualifiés complets dans votre code.</span><span class="sxs-lookup"><span data-stu-id="f2877-119">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="f2877-120">Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="f2877-120">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="f2877-121">Sécurité</span><span class="sxs-lookup"><span data-stu-id="f2877-121">Security</span></span>  
 <span data-ttu-id="f2877-122">Si vous déplacez le mot de passe sur un réseau, vous devez utiliser une méthode sécurisée pour transférer des données.</span><span class="sxs-lookup"><span data-stu-id="f2877-122">If you are moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="f2877-123">Pour plus d’informations, consultez [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc).</span><span class="sxs-lookup"><span data-stu-id="f2877-123">For more information, see [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc).</span></span>  
  
 <span data-ttu-id="f2877-124">Vous pouvez améliorer la précision de la `ValidatePassword` fonction en ajoutant des contrôles de complexité supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="f2877-124">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
-   <span data-ttu-id="f2877-125">Comparez le mot de passe et ses sous-chaînes un dictionnaire défini par l’application, identificateur d’utilisateur et le nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f2877-125">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="f2877-126">En outre, considérez les caractères visuellement semblables comme équivalents lorsque vous effectuez des comparaisons.</span><span class="sxs-lookup"><span data-stu-id="f2877-126">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="f2877-127">Par exemple, considérez les lettres « l » et « e » comme équivalentes aux chiffres « 1 » et « 3 ».</span><span class="sxs-lookup"><span data-stu-id="f2877-127">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
-   <span data-ttu-id="f2877-128">S’il n'existe qu’un seul caractère en majuscule, assurez-vous qu’il n’est pas premier caractère du mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f2877-128">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
-   <span data-ttu-id="f2877-129">Assurez-vous que les deux derniers caractères du mot de passe sont des lettres.</span><span class="sxs-lookup"><span data-stu-id="f2877-129">Make sure that the last two characters of the password are letter characters.</span></span>  
  
-   <span data-ttu-id="f2877-130">N’autorisez pas les mots de passe dans lequel tous les symboles sont entrés à partir de la ligne supérieure du clavier.</span><span class="sxs-lookup"><span data-stu-id="f2877-130">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2877-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2877-131">See Also</span></span>  
 <span data-ttu-id="f2877-132"><xref:System.Text.RegularExpressions.Regex></xref:System.Text.RegularExpressions.Regex></span><span class="sxs-lookup"><span data-stu-id="f2877-132"><xref:System.Text.RegularExpressions.Regex></span></span>   
<span data-ttu-id="f2877-133"> [Sécurité des applications web ASP.NET](https://msdn.microsoft.com/library/330a99hc)</span><span class="sxs-lookup"><span data-stu-id="f2877-133"> [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc)</span></span>
