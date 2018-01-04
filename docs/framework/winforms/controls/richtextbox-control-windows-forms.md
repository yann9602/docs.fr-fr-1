---
title: "RichTextBox, contrôle (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text boxes
- RichTextBox control [Windows Forms]
- rich edit controls
ms.assetid: 3225f2ef-c6d9-4bd4-9d3e-2219e58edbf2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4325fd3eb2e3d7179ddb5270d073c7ba5f0f383f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="richtextbox-control-windows-forms"></a><span data-ttu-id="aae2c-102">RichTextBox, contrôle (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="aae2c-102">RichTextBox Control (Windows Forms)</span></span>
<span data-ttu-id="aae2c-103">Windows Forms `RichTextBox` contrôle est utilisé pour l’affichage, la saisie et la manipulation de texte avec mise en forme.</span><span class="sxs-lookup"><span data-stu-id="aae2c-103">The Windows Forms `RichTextBox` control is used for displaying, entering, and manipulating text with formatting.</span></span> <span data-ttu-id="aae2c-104">Le `RichTextBox` contrôle effectue tout le <xref:System.Windows.Forms.TextBox> effectue, mais il peut également afficher des polices, couleurs et des liens ; charger du texte et des images incorporées à partir d’un fichier ; l’annulation et la restauration par progression de la modification des opérations ; et rechercher les caractères spécifiés.</span><span class="sxs-lookup"><span data-stu-id="aae2c-104">The `RichTextBox` control does everything the <xref:System.Windows.Forms.TextBox> control does, but it can also display fonts, colors, and links; load text and embedded images from a file; undo and redo editing operations; and find specified characters.</span></span> <span data-ttu-id="aae2c-105">Le `RichTextBox` contrôle est généralement utilisé pour fournir la manipulation du texte et afficher les fonctionnalités similaires aux applications de traitement de texte tel que Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="aae2c-105">The `RichTextBox` control is typically used to provide text manipulation and display features similar to word processing applications such as Microsoft Word.</span></span> <span data-ttu-id="aae2c-106">Comme le <xref:System.Windows.Forms.TextBox> (contrôle), le `RichTextBox` contrôle peut afficher les barres de défilement ; mais contrairement à la <xref:System.Windows.Forms.TextBox> contrôle, il affiche des barres de défilement horizontal et vertical par défaut et comporte des paramètres de barre de défilement supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="aae2c-106">Like the <xref:System.Windows.Forms.TextBox> control, the `RichTextBox` control can display scroll bars; but unlike the <xref:System.Windows.Forms.TextBox> control, it displays both horizontal and vertical scrollbars by default and has additional scrollbar settings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aae2c-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="aae2c-107">In This Section</span></span>  
 [<span data-ttu-id="aae2c-108">Vue d’ensemble du contrôle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="aae2c-108">RichTextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md)  
 <span data-ttu-id="aae2c-109">Présente les concepts généraux de le `RichTextBox` contrôle, ce qui permet aux utilisateurs d’entrer, afficher et de manipuler du texte avec les options de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="aae2c-109">Introduces the general concepts of the `RichTextBox` control, which allows users to enter, display, and manipulate text with formatting options.</span></span>  
  
 [<span data-ttu-id="aae2c-110">Guide pratique pour déterminer le moment où les attributs de mise en forme changent dans le contrôle RichTextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aae2c-110">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/determine-when-formatting-attributes-change-wf-richtextbox-control.md)  
 <span data-ttu-id="aae2c-111">Explique comment effectuer le suivi des modifications de police et de mise en forme dans le `RichTextBox` contrôle.</span><span class="sxs-lookup"><span data-stu-id="aae2c-111">Explains how to keep track of changes in font and paragraph formatting in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="aae2c-112">Guide pratique pour afficher les barres de défilement dans le contrôle RichTextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aae2c-112">How to: Display Scroll Bars in the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="aae2c-113">Décrit les nombreuses options disponibles pour les barres de défilement dans le `RichTextBox` contrôle.</span><span class="sxs-lookup"><span data-stu-id="aae2c-113">Describes the many choices available for scroll bars in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="aae2c-114">Guide pratique pour afficher des liens de style Web avec le contrôle RichTextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aae2c-114">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="aae2c-115">Explique comment créer des liens vers des sites Web à partir de la `RichTextBox` contrôle.</span><span class="sxs-lookup"><span data-stu-id="aae2c-115">Explains how to link to Web sites from the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="aae2c-116">Guide pratique pour activer les opérations glisser-déplacer avec le contrôle RichTextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aae2c-116">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/enable-drag-and-drop-operations-with-wf-richtextbox-control.md)  
 <span data-ttu-id="aae2c-117">Fournit des instructions pour faire glisser des données dans le `RichTextBox` contrôle.</span><span class="sxs-lookup"><span data-stu-id="aae2c-117">Provides instructions for dragging data into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="aae2c-118">Guide pratique pour charger des fichiers dans le contrôle RichTextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aae2c-118">How to: Load Files into the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-load-files-into-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="aae2c-119">Fournit des instructions pour le chargement d’un fichier existant dans le `RichTextBox` contrôle.</span><span class="sxs-lookup"><span data-stu-id="aae2c-119">Provides instructions for loading an existing file into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="aae2c-120">Guide pratique pour enregistrer des fichiers avec le contrôle RichTextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aae2c-120">How to: Save Files with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-save-files-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="aae2c-121">Fournit des instructions pour l’enregistrement du contenu de la `RichTextBox` contrôle dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="aae2c-121">Provides instructions for saving the contents of the `RichTextBox` control to a file.</span></span>  
  
 [<span data-ttu-id="aae2c-122">Guide pratique pour définir les attributs de police du contrôle RichTextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aae2c-122">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="aae2c-123">Explique comment définir la famille de polices, la taille, style et couleur du texte dans le `RichTextBox` contrôle.</span><span class="sxs-lookup"><span data-stu-id="aae2c-123">Describes how to set the font family, size, style, and color of text in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="aae2c-124">Guide pratique pour définir les retraits, les retraits négatifs de première ligne et les listes à puces avec le contrôle RichTextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aae2c-124">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md)  
 <span data-ttu-id="aae2c-125">Décrit la mise en forme des paragraphes dans le `RichTextBox` contrôle.</span><span class="sxs-lookup"><span data-stu-id="aae2c-125">Describes how to format paragraphs in the `RichTextBox` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="aae2c-126">Référence</span><span class="sxs-lookup"><span data-stu-id="aae2c-126">Reference</span></span>  
 <span data-ttu-id="aae2c-127">Classe <xref:System.Windows.Forms.RichTextBox></span><span class="sxs-lookup"><span data-stu-id="aae2c-127"><xref:System.Windows.Forms.RichTextBox> class</span></span>  
 <span data-ttu-id="aae2c-128">Décrit cette classe et fournit des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="aae2c-128">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aae2c-129">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="aae2c-129">Related Sections</span></span>  
 [<span data-ttu-id="aae2c-130">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aae2c-130">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="aae2c-131">Fournit une liste complète de contrôles Windows Forms, avec des liens vers des informations sur leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="aae2c-131">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="aae2c-132">TextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="aae2c-132">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)  
 <span data-ttu-id="aae2c-133">Présente les concepts généraux de le <xref:System.Windows.Forms.TextBox> contrôle, ce qui permet des modifiable multiligne d’entrer des données à partir de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="aae2c-133">Introduces the general concepts of the <xref:System.Windows.Forms.TextBox> control, which allows editable, multiline input from the user.</span></span>
