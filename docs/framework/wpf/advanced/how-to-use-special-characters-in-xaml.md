---
title: "Guide pratique pour utiliser des caractères spéciaux en XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 308b2152f98286ba532a15e5491b5d1a25aa66dd
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="6c908-102">Guide pratique pour utiliser des caractères spéciaux en XAML</span><span class="sxs-lookup"><span data-stu-id="6c908-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="6c908-103">Les fichiers de balisage qui sont créés dans [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] sont automatiquement enregistrées dans les [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] format de fichier UTF-8, ce qui signifie que les caractères plus spéciaux, tels que des marques d’accentuation, sont encodés correctement.</span><span class="sxs-lookup"><span data-stu-id="6c908-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="6c908-104">Toutefois, il existe un ensemble de caractères spéciaux couramment utilisés qui sont gérés différemment.</span><span class="sxs-lookup"><span data-stu-id="6c908-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="6c908-105">Ces caractères spéciaux suivent la [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard pour l’encodage.</span><span class="sxs-lookup"><span data-stu-id="6c908-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)][!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="6c908-106">Le tableau suivant montre la syntaxe pour l’encodage de ce jeu de caractères spéciaux :</span><span class="sxs-lookup"><span data-stu-id="6c908-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="6c908-107">Caractère</span><span class="sxs-lookup"><span data-stu-id="6c908-107">Character</span></span>|<span data-ttu-id="6c908-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c908-108">Syntax</span></span>|<span data-ttu-id="6c908-109">Description</span><span class="sxs-lookup"><span data-stu-id="6c908-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`<`|<span data-ttu-id="6c908-110">Signe Inférieur à.</span><span class="sxs-lookup"><span data-stu-id="6c908-110">Less than symbol.</span></span>|  
|>|`>`|<span data-ttu-id="6c908-111">Signe Supérieur à.</span><span class="sxs-lookup"><span data-stu-id="6c908-111">Greater than sign.</span></span>|  
|&|`&`|<span data-ttu-id="6c908-112">Symbole de Et commercial.</span><span class="sxs-lookup"><span data-stu-id="6c908-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="6c908-113">"</span><span class="sxs-lookup"><span data-stu-id="6c908-113">"</span></span>|`"`|<span data-ttu-id="6c908-114">Symbole de guillemet double.</span><span class="sxs-lookup"><span data-stu-id="6c908-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="6c908-115">Si vous créez des éditeur, un fichier de balisage à l’aide d’un texte tel que [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] le bloc-notes, vous devez enregistrer le fichier dans le [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] le format de fichier UTF-8 afin de préserver les encodé des caractères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="6c908-115">If you create a markup file using a text editor, such as [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="6c908-116">L’exemple suivant montre comment utiliser des caractères spéciaux dans du texte lors de la création du balisage.</span><span class="sxs-lookup"><span data-stu-id="6c908-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c908-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="6c908-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
