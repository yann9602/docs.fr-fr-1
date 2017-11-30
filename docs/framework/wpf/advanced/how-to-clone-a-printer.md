---
title: "Comment : cloner une imprimante"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- print queues [WPF]
- cloning printers [WPF]
- printers [WPF], cloning
- print queues [WPF], cloning
- cloning print queues [WPF]
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 303cb9c1c5b6521839987a56cdc008eac0559cf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-clone-a-printer"></a><span data-ttu-id="92882-102">Comment : cloner une imprimante</span><span class="sxs-lookup"><span data-stu-id="92882-102">How to: Clone a Printer</span></span>
<span data-ttu-id="92882-103">La plupart des entreprises, à un moment donné, d’acheter plusieurs imprimantes du même modèle.</span><span class="sxs-lookup"><span data-stu-id="92882-103">Most businesses will, at some point, buy multiple printers of the same model.</span></span> <span data-ttu-id="92882-104">En général, celles-ci sont toutes installées avec les paramètres de configuration quasiment identiques.</span><span class="sxs-lookup"><span data-stu-id="92882-104">Typically, these are all installed with virtually identical configuration settings.</span></span> <span data-ttu-id="92882-105">L’installation de chaque imprimante peut prendre du temps et sujet aux erreurs.</span><span class="sxs-lookup"><span data-stu-id="92882-105">Installing each printer can be time-consuming and error prone.</span></span> <span data-ttu-id="92882-106">Le <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> espace de noms et le <xref:System.Printing.PrintServer.InstallPrintQueue%2A> classe qui sont exposés avec [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] rend possible d’installer instantanément n’importe quel nombre de files d’attente à l’impression supplémentaires qui sont clonés à partir d’une file d’attente d’impression existant.</span><span class="sxs-lookup"><span data-stu-id="92882-106">The <xref:System.Printing.IndexedProperties?displayProperty=nameWithType> namespace and the <xref:System.Printing.PrintServer.InstallPrintQueue%2A> class that are exposed with [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] makes it possible to instantly install any number of additional print queues that are cloned from an existing print queue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92882-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="92882-107">Example</span></span>  
 <span data-ttu-id="92882-108">Dans l’exemple ci-dessous, une deuxième file d’attente d’impression est cloné à partir d’une file d’attente d’impression existant.</span><span class="sxs-lookup"><span data-stu-id="92882-108">In the example below, a second print queue is cloned from an existing print queue.</span></span> <span data-ttu-id="92882-109">La seconde est différente de la première uniquement dans son nom, un emplacement, un port et un état partagé.</span><span class="sxs-lookup"><span data-stu-id="92882-109">The second differs from the first only in its name, location, port, and shared status.</span></span> <span data-ttu-id="92882-110">Voici les principales étapes de cette opération.</span><span class="sxs-lookup"><span data-stu-id="92882-110">The major steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="92882-111">Créer un <xref:System.Printing.PrintQueue> objet pour l’imprimante existante qui va être clonée.</span><span class="sxs-lookup"><span data-stu-id="92882-111">Create a <xref:System.Printing.PrintQueue> object for the existing printer that is going to be cloned.</span></span>  
  
2.  <span data-ttu-id="92882-112">Créer un <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> à partir de la <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> de la <xref:System.Printing.PrintQueue>.</span><span class="sxs-lookup"><span data-stu-id="92882-112">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A> of the <xref:System.Printing.PrintQueue>.</span></span> <span data-ttu-id="92882-113">Le <xref:System.Collections.DictionaryEntry.Value%2A> propriété de chaque entrée de ce dictionnaire est un objet de l’un des types dérivés de <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="92882-113">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span> <span data-ttu-id="92882-114">Il existe deux façons de définir la valeur d’une entrée dans ce dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="92882-114">There are two ways to set the value of an entry in this dictionary.</span></span>  
  
    -   <span data-ttu-id="92882-115">Utiliser le dictionnaire **supprimer** et <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> méthodes pour supprimer l’entrée, puis ajoutez-le de nouveau avec la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="92882-115">Use the dictionary's **Remove** and <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A> methods to remove the entry and then re-add it with the desired value.</span></span>  
  
    -   <span data-ttu-id="92882-116">Utiliser le dictionnaire <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="92882-116">Use the dictionary's <xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A> method.</span></span>  
  
     <span data-ttu-id="92882-117">L’exemple suivant illustre deux façons.</span><span class="sxs-lookup"><span data-stu-id="92882-117">The example below illustrates both ways.</span></span>  
  
3.  <span data-ttu-id="92882-118">Créer un <xref:System.Printing.IndexedProperties.PrintBooleanProperty> et définissez son <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> « IsShared » et ses <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> à `true`.</span><span class="sxs-lookup"><span data-stu-id="92882-118">Create a <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "IsShared" and its <xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A> to `true`.</span></span>  
  
4.  <span data-ttu-id="92882-119">Utilisez le <xref:System.Printing.IndexedProperties.PrintBooleanProperty> objet à la valeur de la <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>de « IsShared » entrée.</span><span class="sxs-lookup"><span data-stu-id="92882-119">Use the <xref:System.Printing.IndexedProperties.PrintBooleanProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "IsShared" entry.</span></span>  
  
5.  <span data-ttu-id="92882-120">Créer un <xref:System.Printing.IndexedProperties.PrintStringProperty> et définissez son <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> « ShareName » et ses <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> aux <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="92882-120">Create a <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "ShareName" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
6.  <span data-ttu-id="92882-121">Utilisez le <xref:System.Printing.IndexedProperties.PrintStringProperty> objet à la valeur de la <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>d’entrée « ShareName ».</span><span class="sxs-lookup"><span data-stu-id="92882-121">Use the <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "ShareName" entry.</span></span>  
  
7.  <span data-ttu-id="92882-122">Création d’une autre <xref:System.Printing.IndexedProperties.PrintStringProperty> et définissez son <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> à « Emplacement » et ses <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> aux <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="92882-122">Create another <xref:System.Printing.IndexedProperties.PrintStringProperty> object and set its <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> to "Location" and its <xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A> to an appropriate <xref:System.String>.</span></span>  
  
8.  <span data-ttu-id="92882-123">Utilisez la deuxième <xref:System.Printing.IndexedProperties.PrintStringProperty> objet à la valeur de la <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>d’entrée « Location ».</span><span class="sxs-lookup"><span data-stu-id="92882-123">Use the second <xref:System.Printing.IndexedProperties.PrintStringProperty> object to be the value of the <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>'s "Location" entry.</span></span>  
  
9. <span data-ttu-id="92882-124">Créer un tableau de <xref:System.String>s.</span><span class="sxs-lookup"><span data-stu-id="92882-124">Create an array of <xref:System.String>s.</span></span> <span data-ttu-id="92882-125">Chaque élément est le nom d’un port sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="92882-125">Each item is the name of a port on the server.</span></span>  
  
10. <span data-ttu-id="92882-126">Utilisez <xref:System.Printing.PrintServer.InstallPrintQueue%2A> pour installer la nouvelle imprimante avec les nouvelles valeurs.</span><span class="sxs-lookup"><span data-stu-id="92882-126">Use <xref:System.Printing.PrintServer.InstallPrintQueue%2A> to install the new printer with the new values.</span></span>  
  
 <span data-ttu-id="92882-127">Il est un exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="92882-127">An example is below.</span></span>  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a><span data-ttu-id="92882-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92882-128">See Also</span></span>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [<span data-ttu-id="92882-129">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="92882-129">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="92882-130">Vue d’ensemble de l’impression</span><span class="sxs-lookup"><span data-stu-id="92882-130">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
