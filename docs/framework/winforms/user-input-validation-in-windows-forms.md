---
title: "Validation des entr&#233;es d&#39;utilisateur dans les Windows Forms | Microsoft Docs"
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
  - "entrée d'utilisateur, valider dans les Windows Forms"
  - "valider les entrées d'utilisateur, Windows Forms"
  - "validation, entrée d'utilisateur (Windows Forms)"
  - "Windows Forms, valider les entrées d'utilisateur"
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Validation des entr&#233;es d&#39;utilisateur dans les Windows Forms
Lorsque les utilisateurs entrent des données dans votre application, vous pouvez vérifier que ces données sont valides avant que votre application ne les utilise.  Vous pouvez exiger que certains champs de texte ne soient pas de longueur nulle, qu'un champ soit au format d'un numéro de téléphone ou d'un autre type de données, ou qu'une chaîne ne contienne pas de caractères potentiellement dangereux, capables de compromettre la sécurité d'une base de données.  Windows Forms propose plusieurs méthodes pour valider l'entrée dans votre application.  
  
## Validation avec le contrôle MaskedTextBox  
 Si vous devez forcer les utilisateurs à entrer des données dans un format précis, comme un numéro de téléphone ou un numéro de pièce, vous pouvez le faire rapidement et avec une grande économie de code à l'aide du contrôle <xref:System.Windows.Forms.MaskedTextBox>.  Un *masque* est une chaîne composée de caractères d'un langage de masquage qui spécifie quels caractères peuvent être entrés à n'importe quelle position dans la zone de texte.  Le contrôle affiche un jeu d'invites à l'utilisateur.  Si l'utilisateur tape une entrée incorrecte, un caractère au lieu d'un chiffre par exemple, le contrôle rejette automatiquement l'entrée.  
  
 Le langage de masquage utilisé par <xref:System.Windows.Forms.MaskedTextBox> est très flexible.  Il vous permet de spécifier les caractères requis, les caractères facultatifs, les caractères littéraux tels que les traits d'union et les parenthèses, les caractères de monnaie et les séparateurs de date.  Le contrôle fonctionne également bien lorsqu'il est lié à une source de données.  L'événement <xref:System.Windows.Forms.Binding.Format> sur une liaison de données peut être utilisé pour reformater les données entrantes en fonction du masque, et l'événement <xref:System.Windows.Forms.Binding.Parse> pour reformater les données sortantes en fonction des spécifications du champ de données.  
  
 Pour plus d'informations, consultez [MaskedTextBox, contrôle](../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md).  
  
## Validation commandée par événement  
 Si vous souhaitez un contrôle total de la validation par programmation, ou devez exécuter des contrôles de validation complexes, vous devez utiliser les événements de validation intégrés dans la plupart des contrôles Windows Forms.  Chaque contrôle qui accepte les entrées d'utilisateur au format libre a un événement <xref:System.Windows.Forms.Control.Validating> qui se produira chaque fois que le contrôle nécessite une validation de données.  Dans la méthode de gestion d'événement <xref:System.Windows.Forms.Control.Validating>, vous pouvez valider l'entrée d'utilisateur de plusieurs façons.  Par exemple, si vous avez une zone de texte qui doit contenir un code postal, vous pouvez exécuter la validation comme suit :  
  
-   Si le code postal doit appartenir à un groupe spécifique de codes postaux, vous pouvez exécuter une comparaison de chaînes sur l'entrée pour valider les données entrées par l'utilisateur.  Par exemple, si le code postal doit être compris dans le jeu {10001, 10002, 10003}, vous pouvez utiliser une comparaison de chaînes pour valider les données.  
  
-   Si le code postal doit avoir un format spécifique, vous pouvez utiliser des expressions régulières pour valider les données entrées par l'utilisateur.  Par exemple, pour valider le format `#####` ou `#####-####`, vous pouvez utiliser l'expression régulière `^(\d{5})(-\d{4})?$`.  Pour valider le format `A#A #A#`, vous pouvez utiliser l'expression régulière `[A-Z]\d[A-Z] \d[A-Z]\d`.  Pour plus d'informations sur les expressions régulières, consultez [Expressions régulières du .NET Framework](../../../docs/standard/base-types/regular-expressions.md) et [Exemples d'expressions régulières](../../../docs/standard/base-types/regular-expression-examples.md).  
  
-   Si le code postal doit être un code postal valide aux États\-Unis, vous pouvez appeler un service Web de code postal pour valider les données entrées par l'utilisateur.  
  
 L'événement <xref:System.Windows.Forms.Control.Validating> reçoit un objet de type <xref:System.ComponentModel.CancelEventArgs>.  Si vous déterminez que les données du contrôle ne sont pas valides, vous pouvez annuler l'événement <xref:System.Windows.Forms.Control.Validating> en affectant à la propriété <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> de cet objet la valeur `true`.  Si vous ne définissez pas la propriété <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>, Windows Forms partira du principe que la validation a réussi pour ce contrôle, et déclenchera l'événement <xref:System.Windows.Forms.Control.Validated>.  
  
 Pour obtenir un exemple de code qui valide une adresse de messagerie dans un <xref:System.Windows.Controls.TextBox>, consultez <xref:System.Windows.Forms.Control.Validating>.  
  
### Liaison de données et validation commandée par événement  
 La validation est très utile lorsque vous avez lié vos contrôles à une source de données, comme une table de base de données.  La validation vous permet de veiller à ce que les données de votre contrôle soient conformes au format requis par la source de données, et qu'elles ne contiennent pas de caractères spéciaux tels que des guillemets ou des barres obliques inverses potentiellement dangereuses.  
  
 Lorsque vous utilisez la liaison de données, les données dans votre contrôle sont synchronisées avec la source de données pendant l'exécution de l'événement <xref:System.Windows.Forms.Control.Validating>.  Si vous annulez l'événement <xref:System.Windows.Forms.Control.Validating>, les données ne seront pas synchronisées avec la source de données.  
  
> [!IMPORTANT]
>  Si une validation personnalisée a lieu après l'événement <xref:System.Windows.Forms.Control.Validating>, elle n'affecte pas la liaison de données.  Par exemple, si du code dans un événement <xref:System.Windows.Forms.Control.Validated> tente d'annuler la liaison de données, celle\-ci a encore lieu.  Dans ce cas, pour exécuter la validation dans l'événement <xref:System.Windows.Forms.Control.Validated>, remplacez la valeur de la propriété **Mode de mise à jour de la source de données** du contrôle \(**sous \(Databindings\)**\\**\(Avancé\)**\) **OnValidation** par **Never**, puis ajoutez *Control*`.DataBindings["`*\<YOURFIELD\>*`"].WriteValue()` à votre code de validation.  
  
### Validation implicite et explicite  
 À quel moment les données d'un contrôle sont\-elles validées ?  Cela dépend de vous, le développeur.  Vous pouvez utiliser la validation implicite ou la validation explicite, suivant les besoins de votre application.  
  
#### Validation implicite  
 L'approche de la validation implicite valide les données à mesure que l'utilisateur les entre.  Vous pouvez valider les données à mesure qu'elles sont entrées dans un contrôle en lisant les touches utilisées, ou plus communément chaque fois que l'utilisateur déplace le focus d'entrée d'un contrôle au contrôle suivant.  Cette approche est utile lorsque vous souhaitez fournir à l'utilisateur des commentaires immédiats sur les données qu'il utilise.  
  
 Si vous souhaitez utiliser la validation implicite pour un contrôle, vous devez affecter à la propriété <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> de ce contrôle la valeur `true`.  Si vous annulez l'événement <xref:System.Windows.Forms.Control.Validating>, le comportement du contrôle sera déterminé par la valeur que vous avez assignée à <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>.  Si vous avez assigné <xref:System.Windows.Forms.AutoValidate>, l'annulation de l'événement fera que l'événement <xref:System.Windows.Forms.Control.Validated> ne se produira pas.  Le focus d'entrée reste sur le contrôle actuel jusqu'à ce que l'utilisateur propose une entrée valide.  Si vous avez assigné <xref:System.Windows.Forms.AutoValidate>, l'événement <xref:System.Windows.Forms.Control.Validated> ne se produit pas lorsque vous annulez l'événement, mais le focus passe tout de même au nouveau contrôle.  
  
 Assigner <xref:System.Windows.Forms.AutoValidate> à la propriété <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> empêche toute validation implicite.  Pour valider vos contrôles, vous devrez utiliser la validation explicite.  
  
#### Validation explicite  
 L'approche de la validation explicite valide les données à un moment donné.  Vous pouvez valider les données en réponse à une action utilisateur, par exemple lorsqu'il clique sur le bouton Enregistrer ou le lien Suivant.  Lorsque l'action utilisateur se produit, vous pouvez déclencher la validation explicite comme suit :  
  
-   Appelez <xref:System.Windows.Forms.ContainerControl.Validate%2A> pour valider le dernier contrôle qui a perdu le focus.  
  
-   Appelez <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A> pour valider tous les contrôles enfants dans un formulaire ou le contrôle conteneur.  
  
-   Appelez une méthode personnalisée pour valider manuellement les données dans les contrôles.  
  
#### Comportement de validation implicite par défaut pour les contrôles Windows Forms  
 Les différents contrôles Windows Forms ont différentes valeurs par défaut pour leur propriété <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>.  Le tableau suivant affiche les contrôles les plus courants et leurs valeurs par défaut.  
  
|Contrôle|Comportement de validation par défaut|  
|--------------|-------------------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate>|  
|<xref:System.Windows.Forms.PropertyGrid>|Propriété non exposée dans Visual Studio|  
|<xref:System.Windows.Forms.ToolStripContainer>|Propriété non exposée dans Visual Studio|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate>|  
  
## Fermeture du formulaire et substitution de la validation  
 Lorsqu'un contrôle conserve le focus car les données qu'il contient ne sont pas valides, il est impossible de fermer le formulaire parent en utilisant les méthodes courantes, à savoir :  
  
-   En cliquant sur le bouton **Fermer**.  
  
-   En sélectionnant **Fermer** dans le menu **Système**.  
  
-   En appelant par programme la méthode <xref:System.Windows.Forms.Form.Close%2A>.  
  
 Vous pouvez toutefois, dans certains cas, autoriser l'utilisateur à fermer le formulaire, même si les valeurs contenues dans les contrôles ne sont pas valides.  Vous pouvez ignorer la validation et fermer un formulaire contenant des données non valides en créant un gestionnaire pour l'événement <xref:System.Windows.Forms.Form.Closing> du formulaire.  Dans le code, affectez à la propriété <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> la valeur `false`.  Le formulaire est alors fermé.  Pour obtenir des informations supplémentaires et un exemple, consultez <xref:System.Windows.Forms.Form.Closing?displayProperty=fullName>.  
  
> [!NOTE]
>  Si vous suivez cette procédure pour forcer la fermeture du formulaire, toutes les données non enregistrées, contenues dans les contrôles du formulaire, seront définitivement perdues.  Les formulaires modaux ne valident pas le contenu des contrôles lors de leur fermeture.  Vous pouvez utiliser la validation de contrôles pour verrouiller le focus sur un contrôle, mais vous n'avez pas besoin de vous occuper des aspects liés à la fermeture du formulaire.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Control.Validating?displayProperty=fullName>   
 <xref:System.Windows.Forms.Form.Closing?displayProperty=fullName>   
 <xref:System.ComponentModel.CancelEventArgs?displayProperty=fullName>   
 [MaskedTextBox, contrôle](../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)   
 [Exemples d'expressions régulières](../../../docs/standard/base-types/regular-expression-examples.md)