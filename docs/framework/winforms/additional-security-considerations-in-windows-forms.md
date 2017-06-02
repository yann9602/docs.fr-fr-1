---
title: "Consid&#233;rations suppl&#233;mentaires sur la s&#233;curit&#233; des Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "appels d'API, paramètres de la sécurité Windows Forms"
  - "API, appeler"
  - "Presse-papiers, sécuriser l'accès"
  - "sécurité (Windows Forms)"
  - "sécurité (Windows Forms), appeler des API"
  - "API Windows, appeler"
  - "API Windows, appels sécurisés"
  - "API Windows, paramètres de la sécurité Windows Forms"
  - "Windows Forms, appels sécurisés à une API Windows"
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Consid&#233;rations suppl&#233;mentaires sur la s&#233;curit&#233; des Windows Forms
Les paramètres de sécurité du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] peuvent conduire votre application à s'exécuter dans un environnement de confiance partielle différemment de sur votre ordinateur local.  Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] restreint l'accès à ces ressources locales critiques telles que le système de fichiers, le réseau et les API non managées, entre autres.  Les paramètres de sécurité affectent la possibilité d'appeler l'API Microsoft Win32 ou d'autres API ne pouvant pas être vérifiées par le système de sécurité.  La sécurité concerne également d'autres aspects de votre application, comprenant l'accès au fichier et aux données et l'impression.  Pour plus d'informations sur l'accès au fichier et aux données dans un environnement de confiance partielle, consultez [Accès plus sécurisé aux fichiers et aux données dans les Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md).  Pour plus d'informations sur l'impression dans un environnement de confiance partielle, consultez [Impression plus sécurisée dans les Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md).  
  
 Les sections suivantes expliquent comment utiliser le Presse\-papiers, manipuler la fenêtre et appeler l'API Win32 depuis des applications en cours d'exécution dans un environnement de confiance partielle.  
  
## Accès au Presse\-papiers  
 La classe <xref:System.Security.Permissions.UIPermission> contrôle l'accès au Presse\-papiers et la valeur d'énumération <xref:System.Security.Permissions.UIPermissionClipboard> associée indique le niveau d'accès.  Le tableau suivant répertorie les différents niveaux d'autorisation.  
  
|Valeur UIPermissionClipboard|Description|  
|----------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard>|Le Presse\-papiers peut être utilisé sans aucune restriction.|  
|<xref:System.Security.Permissions.UIPermissionClipboard>|Le Presse\-papiers peut être utilisé avec certaines restrictions.  La possibilité de placer des données sur le Presse\-papiers \(opérations des commandes Copier ou Coller\) n'est pas restreinte.  Les contrôles intrinsèques qui acceptent le collage, tels qu'une zone de texte, peuvent accepter les données du Presse\-papiers, mais les contrôles utilisateur ne peuvent pas lire par programme dans le Presse\-papiers.|  
|<xref:System.Security.Permissions.UIPermissionClipboard>|Le Presse\-papiers ne peut pas être utilisé.|  
  
 Par défaut, un accès <xref:System.Security.Permissions.UIPermissionClipboard> est accordé à la zone Intranet local et un accès <xref:System.Security.Permissions.UIPermissionClipboard> est accordé à la zone Internet.  Cela signifie que l'application peut copier des données vers le Presse\-papiers, mais qu'elle ne peut pas coller par programme vers le Presse\-papiers ou lire à partir de celui\-ci.  Ces restrictions empêchent les programmes ne disposant pas d'une confiance totale de lire les données copiées dans le Presse\-papiers par une autre application.  Si votre application requiert un accès total au Presse\-papiers mais si vous ne disposez pas des autorisations requises, vous devez les élever pour votre application.  Pour plus d'informations sur l'élévation d'autorisations, consultez [Administration de stratégie de sécurité générale](http://msdn.microsoft.com/fr-fr/5121fe35-f0e3-402c-94ab-4f35b0a87b4b).  
  
## Manipulation de fenêtres  
 La classe <xref:System.Security.Permissions.UIPermission> contrôle également l'autorisation de manipuler des fenêtres et d'effectuer d'autres actions liées à l'interface utilisateur ; la valeur d'énumération <xref:System.Security.Permissions.UIPermissionWindow> associée indique le niveau d'accès.  Le tableau suivant répertorie les différents niveaux d'autorisation.  
  
 Par défaut, un accès <xref:System.Security.Permissions.UIPermissionWindow> est accordé à la zone Intranet local et un accès <xref:System.Security.Permissions.UIPermissionWindow> est accordé à la zone Internet.  Cela signifie que dans la zone Internet, l'application peut effectuer la plupart des actions liées à la manipulation de fenêtres et à l'interface utilisateur, mais l'apparence de la fenêtre sera modifiée.  La fenêtre modifiée affiche une bulle de notification lors de sa première ouverture. Elle contient le texte de la barre de titre modifié et nécessite un bouton de fermeture dans la barre de titre.  La bulle de notification et la barre de titre indiquent à l'utilisateur de l'application que celle\-ci s'exécute à un niveau de confiance partielle.  
  
|Valeur UIPermissionWindow|Description|  
|-------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow>|Les utilisateurs peuvent utiliser tous les événements de fenêtres et d'entrée d'utilisateur sans restriction.|  
|<xref:System.Security.Permissions.UIPermissionWindow>|Les utilisateurs n'ont accès qu'aux fenêtres de niveau supérieur plus sécurisées et aux sous\-fenêtres plus sécurisées pour dessiner. Par ailleurs, ils peuvent utiliser uniquement les événements liés aux entrées d'utilisateur pour l'interface utilisateur contenue dans ces fenêtres de niveau supérieur et sous\-fenêtres.  Ces fenêtres plus sécurisées sont clairement étiquetées et ont des restrictions de taille minimale et maximale.  Les restrictions empêchent les risques d'usurpation préjudiciables, tels que l'imitation des écrans de connexion au système ou du bureau de système, et restreignent l'accès par programme aux fenêtres parentes, les API liées au focus et l'utilisation du contrôle <xref:System.Windows.Forms.ToolTip>|  
|<xref:System.Security.Permissions.UIPermissionWindow>|Les utilisateurs n'ont accès qu'aux sous\-fenêtres plus sécurisées pour dessiner. Par ailleurs, ils peuvent utiliser uniquement les événements liés aux entrées d'utilisateur pour l'interface utilisateur dans ces sous\-fenêtres.  Un contrôle affiché dans un navigateur est un exemple de sous\-fenêtre plus sécurisée.|  
|<xref:System.Security.Permissions.UIPermissionWindow>|Les utilisateurs ne peuvent pas utiliser n'importe quels événements de fenêtres ou d'interface utilisateur.  Aucune interface utilisateur ne peut être utilisée.|  
  
 Chaque niveau d'autorisation identifié par l'énumération <xref:System.Security.Permissions.UIPermissionWindow> autorise des actions moins nombreuses que le niveau immédiatement supérieur.  Les tableaux suivants indiquent les actions qui sont restreintes par les valeurs <xref:System.Security.Permissions.UIPermissionWindow> et <xref:System.Security.Permissions.UIPermissionWindow>.  Pour connaître les autorisations exactes requises pour chaque membre, consultez la référence relative à ce membre dans la documentation de la bibliothèque de classes .NET Framework.  
  
 L'autorisation <xref:System.Security.Permissions.UIPermissionWindow> restreint les actions répertoriées dans le tableau suivant.  
  
|Composant|Actions restreintes|  
|---------------|-------------------------|  
|<xref:System.Windows.Forms.Application>|-   Définition de la propriété <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A>.|  
|<xref:System.Windows.Forms.Control>|-   Obtention de la propriété <xref:System.Windows.Forms.Control.Parent%2A>.<br />-   Définition de la propriété `Region`.<br />-   Appel de la méthode <xref:System.Windows.Forms.Control.FindForm%2A>, <xref:System.Windows.Forms.Control.Focus%2A>, <xref:System.Windows.Forms.Control.FromChildHandle%2A> et <xref:System.Windows.Forms.Control.FromHandle%2A>, <xref:System.Windows.Forms.Control.PreProcessMessage%2A>, <xref:System.Windows.Forms.Control.ReflectMessage%2A> ou <xref:System.Windows.Forms.Control.SetTopLevel%2A>.<br />-   Appel de la méthode <xref:System.Windows.Forms.Control.GetChildAtPoint%2A> si le contrôle retourné n'est pas un enfant du contrôle appelant.<br />-   Modification du focus du contrôle à l'intérieur d'un contrôle conteneur.|  
|<xref:System.Windows.Forms.Cursor>|-   Définition de la propriété <xref:System.Windows.Forms.Cursor.Clip%2A>.<br />-   Appel à la méthode <xref:System.Windows.Forms.Control.Hide%2A>.|  
|<xref:System.Windows.Forms.DataGrid>|-   Appel à la méthode <xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A>.|  
|<xref:System.Windows.Forms.Form>|-   Obtention de la propriété <xref:System.Windows.Forms.Form.ActiveForm%2A> ou <xref:System.Windows.Forms.Form.MdiParent%2A>.<br />-   Définition de la propriété <xref:System.Windows.Forms.Form.ControlBox%2A>, <xref:System.Windows.Forms.Form.ShowInTaskbar%2A> ou <xref:System.Windows.Forms.Form.TopMost%2A>.<br />-   Définition de la propriété <xref:System.Windows.Forms.Form.Opacity%2A> avec une valeur inférieure à 50 %.<br />-   Affectation par programme de <xref:System.Windows.Forms.FormWindowState> à la propriété <xref:System.Windows.Forms.Form.WindowState%2A>.<br />-   Appel à la méthode <xref:System.Windows.Forms.Form.Activate%2A>.<br />-   Utilisation des valeurs d'énumération <xref:System.Windows.Forms.FormBorderStyle>, <xref:System.Windows.Forms.FormBorderStyle> et <xref:System.Windows.Forms.FormBorderStyle> <xref:System.Windows.Forms.FormBorderStyle>.|  
|<xref:System.Windows.Forms.NotifyIcon>|-   L'utilisation du composant <xref:System.Windows.Forms.NotifyIcon> est complètement restreinte.|  
  
 La valeur <xref:System.Security.Permissions.UIPermissionWindow> restreint les actions répertoriées dans le tableau suivant en plus des restrictions placées par la valeur <xref:System.Security.Permissions.UIPermissionWindow>.  
  
|Composant|Actions restreintes|  
|---------------|-------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|-   Affichage d'une boîte de dialogue dérivée de la classe <xref:System.Windows.Forms.CommonDialog>.|  
|<xref:System.Windows.Forms.Control>|-   Appel à la méthode <xref:System.Windows.Forms.Control.CreateGraphics%2A>.<br />-   Définition de la propriété <xref:System.Windows.Forms.Control.Cursor%2A>.|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-   Définition de la propriété <xref:System.Windows.Forms.Cursor.Current%2A>.|  
|<xref:System.Windows.Forms.MessageBox>|-   Appel à la méthode <xref:System.Windows.Forms.Form.Show%2A>.|  
  
### Hébergement de contrôles tiers  
 Un autre type de manipulation de fenêtre peut se produire si vos formulaires hébergent des contrôles tiers.  Un contrôle tiers est tout <xref:System.Windows.Forms.UserControl> personnalisé que vous n'avez pas développé et compilé vous\-même.  Bien que le scénario d'hébergement soit difficile à exploiter, il est théoriquement possible pour un contrôle tiers de développer sa surface de rendu pour couvrir l'intégralité de la zone de votre formulaire.  Ce contrôle pourrait ensuite reproduire une boîte de dialogue critique et demander des informations, telles que les combinaisons nom d'utilisateur\/mot de passe ou les numéros de comptes bancaires de vos utilisateurs.  
  
 Pour limiter ce risque potentiel, utilisez uniquement des contrôles tiers provenant de fournisseurs en qui vous pouvez avoir confiance.  Si vous utilisez des contrôles tiers que vous avez téléchargés d'une source non vérifiable, nous vous recommandons d'examiner le code source à la recherche d'attaques éventuelles.  Après avoir vérifié que la source n'est pas nuisible, vous devez compiler l'assembly vous\-même pour garantir que la source correspond à l'assembly.  
  
## Appels API Win32  
 Si la conception de votre application exige l'appel d'une fonction à partir d'une API Win32, vous accédez à du code non managé.  Dans ce cas, les actions du code dans la fenêtre ou le système d'exploitation ne peuvent pas être déterminées lorsque vous utilisez les appels ou les valeurs de l'API Win32.  La classe <xref:System.Security.Permissions.SecurityPermission> et la valeur <xref:System.Security.Permissions.SecurityPermissionFlag> de l'énumération <xref:System.Security.Permissions.SecurityPermissionFlag> contrôlent l'accès au code non managé.  Une application peut accéder uniquement au code non managé lorsque l'autorisation <xref:System.Security.Permissions.SecurityPermissionFlag> lui est accordée.  Par défaut, seules applications qui s'exécutent localement peuvent appeler du code non managé.  
  
 Certains membres Windows Forms fournissent un accès non managé nécessitant une autorisation <xref:System.Security.Permissions.SecurityPermissionFlag>.  Le tableau suivant répertorie les membres dans l'espace de noms <xref:System.Windows.Forms> nécessitant une autorisation.  Pour plus d'informations sur les autorisations requises pour un membre, consultez la documentation de la bibliothèque de classes .NET Framework.  
  
|Composant|Membre|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|-   Méthode <xref:System.Windows.Forms.Application.AddMessageFilter%2A><br />-   Propriété <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A><br />-   Méthode `Exit`<br />-   Méthode <xref:System.Windows.Forms.Application.ExitThread%2A><br />-   Événement <xref:System.Windows.Forms.Application.ThreadException>|  
|<xref:System.Windows.Forms.CommonDialog>|-   Méthode <xref:System.Windows.Forms.CommonDialog.HookProc%2A><br />-   Méthode <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A><br />-   Méthode <xref:System.Windows.Forms.CommonDialog.Reset%2A><br />-   Méthode <xref:System.Windows.Forms.CommonDialog.RunDialog%2A>|  
|<xref:System.Windows.Forms.Control>|-   Méthode <xref:System.Windows.Forms.Control.CreateParams%2A><br />-   Méthode <xref:System.Windows.Forms.Control.DefWndProc%2A><br />-   Méthode <xref:System.Windows.Forms.Control.DestroyHandle%2A><br />-   Méthode <xref:System.Windows.Forms.Control.WndProc%2A>|  
|<xref:System.Windows.Forms.Help>|-   Méthodes <xref:System.Windows.Forms.Help.ShowHelp%2A><br />-   Méthode <xref:System.Windows.Forms.Help.ShowHelpIndex%2A>|  
|<xref:System.Windows.Forms.NativeWindow>|-   Classe <xref:System.Windows.Forms.NativeWindow>|  
|<xref:System.Windows.Forms.Screen>|-   Méthode <xref:System.Windows.Forms.Screen.FromHandle%2A>|  
|<xref:System.Windows.Forms.SendKeys>|-   Méthode <xref:System.Windows.Forms.SendKeys.Send%2A><br />-   Méthode <xref:System.Windows.Forms.SendKeys.SendWait%2A>|  
  
 Si votre application n'est pas autorisée à appeler du code non managé, elle nécessite l'autorisation <xref:System.Security.Permissions.SecurityPermissionFlag> ; sinon vous devez envisager d'autres moyens d'implémenter des fonctionnalités. Dans la plupart des cas, Windows Forms fournit une alternative managée aux fonctions de l'API Win32.  En l'absence d'alternative et si l'application doit accéder à du code non managé, vous devez élever les autorisations pour l'application.  
  
 L'autorisation d'appeler du code non managé permet à une application d'exécuter pratiquement toutes les tâches.  Par conséquent, l'autorisation permettant d'appeler du code non managé doit être uniquement accordée aux applications qui proviennent d'une source fiable.  Sinon, selon l'application, la fonctionnalité d'application qui appelle le code non managé peut être facultative ou activée uniquement dans un environnement de confiance totale.  Pour plus d'informations sur les autorisations à risque, consultez [Dangerous Permissions and Policy Administration](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md).  Pour plus d'informations sur l'élévation d'autorisations, consultez [NIB: General Security Policy Administration](http://msdn.microsoft.com/fr-fr/5121fe35-f0e3-402c-94ab-4f35b0a87b4b).  
  
## Voir aussi  
 [Accès plus sécurisé aux fichiers et aux données dans les Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)   
 [Impression plus sécurisée dans les Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)   
 [Vue d'ensemble de la sécurité dans les Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)   
 [Sécurité des Windows Forms](../../../docs/framework/winforms/windows-forms-security.md)   
 [Sécurisation des applications ClickOnce](../Topic/Securing%20ClickOnce%20Applications.md)