---
title: "Déploiement d’applications faisant référencent au composant PrintForm (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 016643329d2ee66ca5a32f155cf91e0ee137f38f
ms.lasthandoff: 03/13/2017

---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a>Déploiement d’applications faisant référencent au composant PrintForm (Visual Basic)
Si vous souhaitez déployer une application qui référence le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant, le composant doit être installé sur l’ordinateur de destination.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
 Les contrôles PowerPack ne sont plus inclus dans Visual Studio, mais vous pouvez les télécharger à partir du [Centre de téléchargement](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="installing-the-printform-as-a-prerequisite"></a>Installation de PrintForm en tant que composant requis  
 Pour déployer une application, vous devez également déployer tous les composants qui sont référencés par l’application. Le processus d’installation des composants prérequis est connu sous le nom d’ *amorçage*.  
  
 Lorsque le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant est installé sur votre ordinateur de développement, un package de programme d’amorçage de Microsoft Visual Basic Power Packs est ajouté à la [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] répertoire du programme d’amorçage.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Ce package est alors disponible lorsque vous suivez les procédures d’ajout de conditions préalables pour le [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] ou le déploiement de Windows Installer.  
  
 Par défaut, les composants d’amorçage sont déployés à partir du même emplacement que le package d’installation. Vous pouvez également déployer les composants à partir d’une URL ou d’un emplacement de partage de fichiers, à partir duquel les utilisateurs peuvent les télécharger si nécessaire.  
  
> [!NOTE]
>  Pour installer les composants d’amorçage, l’utilisateur peut avoir besoin d’autorisations d’administration ou d’autorisations similaires sur l’ordinateur. Pour [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] applications, cela signifie que l’utilisateur a besoin d’autorisations administratives pour installer l’application, quel que soit le niveau de sécurité spécifié par l’application. Une fois l’application installée, l’utilisateur peut exécuter l’application sans autorisations d’administration.  
  
 Pendant l’installation, les utilisateurs seront invités à installer le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant si elle n’est pas présent sur l’ordinateur de destination.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
 Comme alternative à l’amorçage, vous pouvez pré-déployer le <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>composant à l’aide d’un système de distribution électronique de logiciels tels que Microsoft Systems Management Server.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : installer les composants requis avec une Application ClickOnce](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5)   
 [PrintForm, composant](../../../visual-basic/developing-apps/printing/printform-component.md)
