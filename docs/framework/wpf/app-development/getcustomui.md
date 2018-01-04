---
title: GetCustomUI
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88c2873a5929e25335b0c6ef64f8121e31177ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getcustomui"></a>GetCustomUI
Appelée par PresentationHost.exe pour obtenir des messages d’erreur et d’avancement personnalisés à partir de l’ordinateur hôte, si implémenté.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pwzProgressAssemblyName`  
  
 [out] Pointeur vers l’assembly qui contient l’interface utilisateur fournie par l’hôte de progression.  
  
 `pwzProgressClassName`  
  
 [out] Le nom de la classe qui est l’interface utilisateur d’avancement fournie par l’hôte, de préférence un [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] de fichiers avec <xref:System.Windows.Controls.Page> comme élément de niveau supérieur. Cette classe se trouve dans l’assembly spécifié par `pwzProgressAssemblyName`.  
  
 `pwzErrorAssemblyName`  
  
 [out] Pointeur vers l’assembly qui contient l’interface utilisateur d’erreur fourni par l’hôte.  
  
 `pwzErrorClassName`  
  
 [out] Le nom de la classe qui est l’utilisateur d’erreur fourni par l’hôte de l’interface, de préférence un fichier XAML avec <xref:System.Windows.Controls.Page> comme élément de niveau supérieur. Cette classe se trouve dans l’assembly spécifié par `pwzErrorAssemblyName`.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 HRESULT : ignoré.  
  
## <a name="remarks"></a>Notes  
 Une application hôte peut avoir un thème spécifique ne soit pas conforme à des interfaces utilisateur de PresentationHost.exe par défaut. Si c’est le cas, l’application hôte peut implémenter [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) pour retourner la progression et erreur des interfaces utilisateur à PresentationHost.exe. PresentationHost.exe appelle toujours [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) avant d’utiliser ses interfaces d’utilisateur par défaut.  
  
 Cette fonction est appelée une fois au cours de l’initialisation de PresentationHost.  
  
## <a name="see-also"></a>Voir aussi  
 [IWpfHostSupport](../../../../docs/framework/wpf/app-development/iwpfhostsupport.md)
