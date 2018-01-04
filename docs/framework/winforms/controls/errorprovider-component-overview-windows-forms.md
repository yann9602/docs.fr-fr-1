---
title: Vue d'ensemble du composant ErrorProvider (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 589735156ad4d6d639c2449d6bd693e2b3a32d50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="errorprovider-component-overview-windows-forms"></a>Vue d'ensemble du composant ErrorProvider (Windows Forms)
Windows Forms [ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-windows-forms.md) composant est utilisé pour valider l’entrée d’utilisateur sur un formulaire ou un contrôle. Il est généralement utilisé conjointement avec la validation des entrées d’utilisateur sur un formulaire ou l’affichage des erreurs dans un jeu de données. Un fournisseur d’erreur est une meilleure alternative que l’affichage d’un message d’erreur dans une boîte de message, car une fois qu’un message est fermé, le message d’erreur n’est plus visible. Le <xref:System.Windows.Forms.ErrorProvider> composant affiche une icône d’erreur (![icône ErrorProvider](../../../../docs/framework/winforms/controls/media/vberrorprovidericon.gif "vbErrorProviderIcon")) en regard du contrôle concerné, tel qu’une zone de texte ; lorsque l’utilisateur positionne le pointeur de la souris sur le icône d’erreur, une info-bulle apparaît et affiche la chaîne du message d’erreur.  
  
## <a name="key-properties"></a>Propriétés de clé  
 Le <xref:System.Windows.Forms.ErrorProvider> sont des propriétés de clé du composant <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>, et <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. Lorsque vous utilisez <xref:System.Windows.Forms.ErrorProvider> composant avec des contrôles liés aux données, le <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> propriété doit être définie pour le conteneur approprié (en règle générale le formulaire Windows) afin que le composant affiche une icône d’erreur sur le formulaire. Lorsque le composant est ajouté dans le concepteur, le <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> est définie sur le formulaire conteneur ; si vous ajoutez le contrôle dans le code, vous devez la définir vous-même.  
  
 Le <xref:System.Windows.Forms.ErrorProvider.Icon%2A> propriété peut être définie sur une icône d’erreur personnalisée au lieu de la valeur par défaut. Lorsque le <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> propriété est définie, le <xref:System.Windows.Forms.ErrorProvider> composant peut afficher des messages d’erreur pour un jeu de données. La méthode clé pour la <xref:System.Windows.Forms.ErrorProvider> composant est le <xref:System.Windows.Forms.ErrorProvider.SetError%2A> méthode, qui spécifie la chaîne du message d’erreur et l’emplacement où doit apparaître l’icône d’erreur.  
  
> [!NOTE]
>  Le <xref:System.Windows.Forms.ErrorProvider> composant ne fournit pas de prise en charge intégrée pour les clients d’accessibilité. Pour rendre votre application accessible lors de l’utilisation de ce composant, vous devez fournir un mécanisme de commentaires supplémentaire, accessible.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ErrorProvider>  
 [Guide pratique pour afficher des erreurs d'un groupe de données à l'aide du composant ErrorProvider Windows Forms](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)  
 [Guide pratique pour afficher des icônes d’erreur pour la validation de formulaire à l’aide du composant ErrorProvider Windows Forms](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
