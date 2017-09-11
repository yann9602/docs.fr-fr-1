---
title: Modules (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- modules, Visual Basic
ms.assetid: 370bfc90-e8f2-4942-bdec-9897ce605d31
caps.latest.revision: 11
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
ms.openlocfilehash: 808510c83339e1768dba39f119a2e97ac44f0e4a
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="modules-visual-basic"></a><span data-ttu-id="265d4-102">Modules (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="265d4-102">Modules (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="265d4-103">fournit plusieurs modules qui vous permettent de simplifier les tâches courantes dans votre code, notamment la manipulation de chaînes, effectuer des calculs mathématiques, l’obtention d’informations système, opérations de fichier et répertoire et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="265d4-103"> provides several modules that enable you to simplify common tasks in your code, including manipulating strings, performing mathematical calculations, getting system information, performing file and directory operations, and so on.</span></span> <span data-ttu-id="265d4-104">Le tableau suivant répertorie les modules fournis par [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="265d4-104">The following table lists the modules provided by [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="265d4-105"><xref:Microsoft.VisualBasic.Constants></xref:Microsoft.VisualBasic.Constants></span><span class="sxs-lookup"><span data-stu-id="265d4-105"><xref:Microsoft.VisualBasic.Constants></span></span>|<span data-ttu-id="265d4-106">Contient diverses constantes.</span><span class="sxs-lookup"><span data-stu-id="265d4-106">Contains miscellaneous constants.</span></span> <span data-ttu-id="265d4-107">Ces constantes peuvent être utilisées n’importe où dans votre code.</span><span class="sxs-lookup"><span data-stu-id="265d4-107">These constants can be used anywhere in your code.</span></span>|  
|<span data-ttu-id="265d4-108"><xref:Microsoft.VisualBasic.ControlChars></xref:Microsoft.VisualBasic.ControlChars></span><span class="sxs-lookup"><span data-stu-id="265d4-108"><xref:Microsoft.VisualBasic.ControlChars></span></span>|<span data-ttu-id="265d4-109">Contient des caractères de contrôle constants pour l’impression et l’affichage du texte.</span><span class="sxs-lookup"><span data-stu-id="265d4-109">Contains constant control characters for printing and displaying text.</span></span>|  
|<span data-ttu-id="265d4-110"><xref:Microsoft.VisualBasic.Conversion></xref:Microsoft.VisualBasic.Conversion></span><span class="sxs-lookup"><span data-stu-id="265d4-110"><xref:Microsoft.VisualBasic.Conversion></span></span>|<span data-ttu-id="265d4-111">Contient des membres qui convertissent les nombres décimaux en d’autres bases, les nombres en chaînes, des chaînes en nombres et données d’un type en un autre.</span><span class="sxs-lookup"><span data-stu-id="265d4-111">Contains members that convert decimal numbers to other bases, numbers to strings, strings to numbers, and one data type to another.</span></span>|  
|<span data-ttu-id="265d4-112"><xref:Microsoft.VisualBasic.DateAndTime></xref:Microsoft.VisualBasic.DateAndTime></span><span class="sxs-lookup"><span data-stu-id="265d4-112"><xref:Microsoft.VisualBasic.DateAndTime></span></span>|<span data-ttu-id="265d4-113">Contient des membres qui obtiennent la date ou l’heure, effectuent des calculs de date, retournent une date ou heure, définissent la date ou l’heure ou la durée d’un processus.</span><span class="sxs-lookup"><span data-stu-id="265d4-113">Contains members that get the current date or time, perform date calculations, return a date or time, set the date or time, or time the duration of a process.</span></span>|  
|<span data-ttu-id="265d4-114"><xref:Microsoft.VisualBasic.ErrObject></xref:Microsoft.VisualBasic.ErrObject></span><span class="sxs-lookup"><span data-stu-id="265d4-114"><xref:Microsoft.VisualBasic.ErrObject></span></span>|<span data-ttu-id="265d4-115">Contient des informations sur les erreurs d’exécution et les méthodes à générer ou de supprimer une erreur.</span><span class="sxs-lookup"><span data-stu-id="265d4-115">Contains information about run-time errors and methods to raise or clear an error.</span></span>|  
|<span data-ttu-id="265d4-116"><xref:Microsoft.VisualBasic.FileSystem></xref:Microsoft.VisualBasic.FileSystem></span><span class="sxs-lookup"><span data-stu-id="265d4-116"><xref:Microsoft.VisualBasic.FileSystem></span></span>|<span data-ttu-id="265d4-117">Contient des membres qui effectuent des opérations de fichier, répertoire ou dossier et système.</span><span class="sxs-lookup"><span data-stu-id="265d4-117">Contains members that perform file, directory or folder, and system operations.</span></span>|  
|<span data-ttu-id="265d4-118"><xref:Microsoft.VisualBasic.Financial></xref:Microsoft.VisualBasic.Financial></span><span class="sxs-lookup"><span data-stu-id="265d4-118"><xref:Microsoft.VisualBasic.Financial></span></span>|<span data-ttu-id="265d4-119">Contient des procédures utilisées pour effectuer des calculs financiers.</span><span class="sxs-lookup"><span data-stu-id="265d4-119">Contains procedures that are used to perform financial calculations.</span></span>|  
|<span data-ttu-id="265d4-120"><xref:Microsoft.VisualBasic.Globals></xref:Microsoft.VisualBasic.Globals></span><span class="sxs-lookup"><span data-stu-id="265d4-120"><xref:Microsoft.VisualBasic.Globals></span></span>|<span data-ttu-id="265d4-121">Contient des informations sur la version actuelle du moteur de script.</span><span class="sxs-lookup"><span data-stu-id="265d4-121">Contains information about the current scripting engine version.</span></span>|  
|<span data-ttu-id="265d4-122"><xref:Microsoft.VisualBasic.Information></xref:Microsoft.VisualBasic.Information></span><span class="sxs-lookup"><span data-stu-id="265d4-122"><xref:Microsoft.VisualBasic.Information></span></span>|<span data-ttu-id="265d4-123">Contient les membres qui retournent, tester ou vérifier des informations telles que la taille du tableau, les noms de types et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="265d4-123">Contains the members that return, test for, or verify information such as array size, type names, and so on.</span></span>|  
|<span data-ttu-id="265d4-124"><xref:Microsoft.VisualBasic.Interaction></xref:Microsoft.VisualBasic.Interaction></span><span class="sxs-lookup"><span data-stu-id="265d4-124"><xref:Microsoft.VisualBasic.Interaction></span></span>|<span data-ttu-id="265d4-125">Contient des membres qui interagissent avec les objets, les applications et les systèmes.</span><span class="sxs-lookup"><span data-stu-id="265d4-125">Contains members interact with objects, applications, and systems.</span></span>|  
|<span data-ttu-id="265d4-126"><xref:Microsoft.VisualBasic.Strings></xref:Microsoft.VisualBasic.Strings></span><span class="sxs-lookup"><span data-stu-id="265d4-126"><xref:Microsoft.VisualBasic.Strings></span></span>|<span data-ttu-id="265d4-127">Contient des membres qui effectuent des opérations de chaînes telles que la remise en forme des chaînes, rechercher une chaîne, en obtenant la longueur d’une chaîne et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="265d4-127">Contains members that perform string operations such as reformatting strings, searching a string, getting the length of a string, and so on.</span></span>|  
|<span data-ttu-id="265d4-128"><xref:Microsoft.VisualBasic.VBMath></xref:Microsoft.VisualBasic.VBMath></span><span class="sxs-lookup"><span data-stu-id="265d4-128"><xref:Microsoft.VisualBasic.VBMath></span></span>|<span data-ttu-id="265d4-129">Contient des membres effectuent des opérations mathématiques.</span><span class="sxs-lookup"><span data-stu-id="265d4-129">Contains members perform mathematical operations.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="265d4-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="265d4-130">See Also</span></span>  
 <span data-ttu-id="265d4-131">[Référence du langage Visual Basic](../../visual-basic/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="265d4-131">[Visual Basic Language Reference](../../visual-basic/language-reference/index.md) </span></span>  
<span data-ttu-id="265d4-132"> [Visual Basic](../../visual-basic/index.md)</span><span class="sxs-lookup"><span data-stu-id="265d4-132"> [Visual Basic](../../visual-basic/index.md)</span></span>
