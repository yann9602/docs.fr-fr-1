---
title: "H&#233;bergement de contenu Win32 dans WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interopérabilité (WPF), didacticiels"
  - "interopérabilité (WPF), Win32"
  - "code Win32, interopérabilité WPF"
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# H&#233;bergement de contenu Win32 dans WPF
## Composants requis  
 Consultez [Interopérabilité WPF et Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
## Une procédure pas à pas de Win32 à l'intérieur de Windows Presentation Framework \(HwndHost\)  
 Pour réutiliser le contenu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] à l'intérieur des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], utilisez <xref:System.Windows.Interop.HwndHost>, qui est un contrôle qui permet à HWND de ressembler à un contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Comme <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> est simple à utiliser : dérivez de <xref:System.Windows.Interop.HwndHost> et implémentez les méthodes `BuildWindowCore` et `DestroyWindowCore`, puis instanciez votre classe dérivée <xref:System.Windows.Interop.HwndHost> et placez\-la à l'intérieur de votre application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Si votre logique [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] est déjà empaquetée comme un contrôle, votre implémentation `BuildWindowCore` n'est guère plus qu'un appel à `CreateWindow`.  Par exemple, pour créer un contrôle LISTBOX [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dans [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] :  
  
```  
virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {  
    HWND handle = CreateWindowEx(0, L"LISTBOX",   
    L"this is a Win32 listbox",  
    WS_CHILD | WS_VISIBLE | LBS_NOTIFY  
    | WS_VSCROLL | WS_BORDER,  
    0, 0, // x, y  
    30, 70, // height, width  
    (HWND) hwndParent.Handle.ToPointer(), // parent hwnd  
    0, // hmenu  
    0, // hinstance  
    0); // lparam  
  
    return HandleRef(this, IntPtr(handle));  
}  
  
virtual void DestroyWindowCore(HandleRef hwnd) override {  
    // HwndHost will dispose the hwnd for us  
}  
```  
  
 Considérons cependant que le code [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ne soit pas tout à fait si autonome ?  Dans ce cas, vous pouvez créer une boîte de dialogue [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] et incorporer son contenu dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] plus grande.  L'exemple illustre ce cas de figure dans [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] et [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], bien qu'il soit également possible dans un langage différent ou à partir de la ligne de commande.  
  
 Commencez avec une simple boîte de dialogue, compilée dans un projet de [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)].  
  
 Introduisez ensuite la boîte de dialogue dans la plus grande application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
-   Compilez la [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] comme managé \(`/clr`\)  
  
-   Transformez la boîte de dialogue en un contrôle  
  
-   Définissez la classe dérivée de <xref:System.Windows.Interop.HwndHost> à l'aide des méthodes `BuildWindowCore` et `DestroyWindowCore`  
  
-   Substituez la méthode `TranslateAccelerator` pour gérer les touches de boîtes de dialogue  
  
-   Substituez la méthode `TabInto` pour prendre en charge la tabulation  
  
-   Substituez la méthode `OnMnemonic` pour prendre en charge les mnémoniques  
  
-   Instanciez la sous\-classe <xref:System.Windows.Interop.HwndHost> et placez\-la sous le bon élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  
  
### Transformez la boîte de dialogue en un contrôle  
 Vous pouvez transformer une boîte de dialogue en un HWND enfant à l'aide des styles WS\_CHILD et DS\_CONTROL.  Allez dans le fichier de ressources \(.rc\) où la boîte de dialogue est définie, et recherchez le début de la définition de la boîte de dialogue :  
  
```  
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121  
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU  
```  
  
 Modifiez comme suit la deuxième ligne :  
  
```  
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL  
```  
  
 Cette action n'en fait pas complètement un contrôle autonome car vous devez encore appeler `IsDialogMessage()` pour que [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] puisse traiter certains messages. Toutefois, la modification du contrôle offre un moyen simple de placer ces contrôles à l'intérieur d'un autre HWND.  
  
## Sous\-classe HwndHost  
 Importez les espaces de noms suivants :  
  
```  
namespace ManagedCpp  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Input;  
    using namespace System::Windows::Media;  
    using namespace System::Runtime::InteropServices;  
```  
  
 Créez ensuite une classe dérivée de <xref:System.Windows.Interop.HwndHost> et substituez les méthodes `BuildWindowCore` et `DestroyWindowCore` :  
  
```  
public ref class MyHwndHost : public HwndHost, IKeyboardInputSink {  
    private:  
        HWND dialog;  
  
    protected:   
        virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {  
            InitializeGlobals();   
            dialog = CreateDialog(hInstance,   
                MAKEINTRESOURCE(IDD_DIALOG1),   
                (HWND) hwndParent.Handle.ToPointer(),  
                (DLGPROC) About);   
            return HandleRef(this, IntPtr(dialog));  
        }  
  
        virtual void DestroyWindowCore(HandleRef hwnd) override {  
            // hwnd will be disposed for us  
        }  
```  
  
 Vous utilisez ici `CreateDialog` pour créer la boîte de dialogue qui est vraiment un contrôle.  Comme il s'agit de l'une des premières méthodes appelée à l'intérieur de la [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], vous devez également procéder à une initialisation [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] standard en appelant une fonction que vous définirez ultérieurement, appelée `InitializeGlobals()` :  
  
```  
bool initialized = false;  
    void InitializeGlobals() {  
        if (initialized) return;  
        initialized = true;  
  
        // TODO: Place code here.  
        MSG msg;  
        HACCEL hAccelTable;  
  
        // Initialize global strings  
        LoadString(hInstance, IDS_APP_TITLE, szTitle, MAX_LOADSTRING);  
        LoadString(hInstance, IDC_TYPICALWIN32DIALOG, szWindowClass, MAX_LOADSTRING);  
        MyRegisterClass(hInstance);  
  
```  
  
### Substituez la méthode TranslateAccelerator pour gérer les touches de boîtes de dialogue  
 Si vous exécutiez maintenant cet exemple, vous obtiendriez un contrôle de boîte de dialogue qui s'affiche, mais qui ignorerait tout du traitement du clavier qui fait d'une boîte de dialogue une boîte de dialogue fonctionnelle.  Vous devez maintenant substituer l'implémentation `TranslateAccelerator` \(laquelle provient de `IKeyboardInputSink`, une interface que <xref:System.Windows.Interop.HwndHost> implémente\).  Cette méthode est appelée lorsque l'application reçoit WM\_KEYDOWN et WM\_SYSKEYDOWN.  
  
```  
  
#undef TranslateAccelerator  
        virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
            ModifierKeys modifiers) override   
        {  
            ::MSG m = ConvertMessage(msg);  
  
            // Win32's IsDialogMessage() will handle most of our tabbing, but doesn't know   
            // what to do when it reaches the last tab stop  
            if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {  
                HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
                HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
                TraversalRequest^ request = nullptr;  
  
                if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {  
                    // this code should work, but there’s a bug with interop shift-tab in current builds                      
                    request = gcnew TraversalRequest(FocusNavigationDirection::Last);  
                }  
                else if (!GetKeyState(VK_SHIFT) && GetFocus() == lastTabStop) {  
                    request = gcnew TraversalRequest(FocusNavigationDirection::Next);  
                }  
  
                if (request != nullptr)  
                    return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);  
  
            }  
  
            // Only call IsDialogMessage for keys it will do something with.  
            if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {  
                switch (m.wParam) {  
                    case VK_TAB:  
                    case VK_LEFT:  
                    case VK_UP:  
                    case VK_RIGHT:  
                    case VK_DOWN:  
                    case VK_EXECUTE:  
                    case VK_RETURN:  
                    case VK_ESCAPE:  
                    case VK_CANCEL:  
                        IsDialogMessage(dialog, &m);  
                        // IsDialogMessage should be called ProcessDialogMessage --  
                        // it processes messages without ever really telling you  
                        // if it handled a specific message or not  
                        return true;  
                }  
            }  
  
            return false; // not a key we handled  
        }  
```  
  
 Face à une telle quantité de code, des explications plus détaillées s'imposent.  En premier lieu, le code qui utilise les macros [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] et [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] ; vous devez savoir qu'il existe déjà une macro appelée `TranslateAccelerator`, définie dans winuser.h :  
  
```  
#define TranslateAccelerator  TranslateAcceleratorW  
```  
  
 Assurez\-vous donc de définir une méthode `TranslateAccelerator` plutôt qu'une méthode `TranslateAcceleratorW`.  
  
 De même, il existe à la fois le winuser.h MSG non managé et le struct `Microsoft::Win32::MSG` managé.  Vous pouvez supprimer l'ambiguïté entre les deux à l'aide de l'opérateur [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::`.  
  
```  
  
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
    ModifierKeys modifiers) override   
{  
    ::MSG m = ConvertMessage(msg);  
```  
  
 Les deux MSG possèdent les mêmes données, mais il est parfois plus facile d'utiliser la définition non managée. Vous pouvez donc, dans cet exemple, définir la routine de conversion évidente :  
  
```  
::MSG ConvertMessage(System::Windows::Interop::MSG% msg) {  
    ::MSG m;  
    m.hwnd = (HWND) msg.hwnd.ToPointer();  
    m.lParam = (LPARAM) msg.lParam.ToPointer();  
    m.message = msg.message;  
    m.wParam = (WPARAM) msg.wParam.ToPointer();  
  
    m.time = msg.time;  
  
    POINT pt;  
    pt.x = msg.pt_x;  
    pt.y = msg.pt_y;  
    m.pt = pt;  
  
    return m;  
}  
```  
  
 Retournez à `TranslateAccelerator`.  Le principe de base est d'appeler la fonction [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] `IsDialogMessage` pour effectuer autant de tâches que possible, mais `IsDialogMessage` n'a accès qu'à la boîte de dialogue. Comme onglet utilisateur autour de la boîte de dialogue, lorsque la tabulation s'exécute après le dernier contrôle dans notre boîte de dialogue, vous devez définir le focus de la partie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en appelant `IKeyboardInputSite::OnNoMoreStops`.  
  
```  
// Win32's IsDialogMessage() will handle most of the tabbing, but doesn't know   
// what to do when it reaches the last tab stop  
if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {  
    HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
    HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
    TraversalRequest^ request = nullptr;  
  
    if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {  
        request = gcnew TraversalRequest(FocusNavigationDirection::Last);  
    }  
    else if (!GetKeyState(VK_SHIFT) && GetFocus() ==  lastTabStop) { {  
        request = gcnew TraversalRequest(FocusNavigationDirection::Next);  
    }  
  
    if (request != nullptr)  
        return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);  
}  
```  
  
 Pour finir, appelez `IsDialogMessage`.  Cependant, l'une des responsabilités d'une méthode `TranslateAccelerator` est d'indiquer à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] si vous avez géré ou non la séquence de touches.  Si vous ne l'avez pas gérée, l'événement d'entrée peut tunneler et se propager à travers le reste de l'application.  Ici, vous exposerez une particularité de la gestion des messages du clavier et la nature de l'architecture d'entrée dans [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  Malheureusement, `IsDialogMessage` n'est pas du tout retourné s'il gère une séquence de touches particulière.  Pire encore, il appellera `DispatchMessage()` en présence de séquences de touches qu'il ne devrait pas gérer \!  Vous allez donc devoir procéder à une ingénierie à rebours de `IsDialogMessage` et l'appeler uniquement pour les touches que vous savez qu'il gérera :  
  
```  
// Only call IsDialogMessage for keys it will do something with.  
if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {  
    switch (m.wParam) {  
        case VK_TAB:  
        case VK_LEFT:  
        case VK_UP:  
        case VK_RIGHT:  
        case VK_DOWN:  
        case VK_EXECUTE:  
        case VK_RETURN:  
        case VK_ESCAPE:  
        case VK_CANCEL:  
            IsDialogMessage(dialog, &m);  
            // IsDialogMessage should be called ProcessDialogMessage --  
            // it processes messages without ever really telling you  
            // if it handled a specific message or not  
            return true;  
    }  
```  
  
### Substituer la méthode TabInto pour prendre en charge la tabulation  
 Maintenant que vous avez implémenté `TranslateAccelerator`, un utilisateur peut tabuler à l'intérieur de la boîte de dialogue et tabuler hors de cette boîte et accéder ainsi à l'application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] plus grande.  Cependant, un utilisateur ne peut pas tabuler en arrière pour retourner dans la boîte de dialogue.  Pour résoudre ce problème, vous substituez `TabInto` :  
  
```  
  
public:   
    virtual bool TabInto(TraversalRequest^ request) override {  
        if (request->FocusNavigationDirection == FocusNavigationDirection::Last) {  
            HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);  
            SetFocus(lastTabStop);  
        }  
        else {  
            HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);  
            SetFocus(firstTabStop);  
        }  
        return true;  
    }  
  
```  
  
 Le paramètre `TraversalRequest` vous indique si l'action de tabulation est générée par la touche Tab ou par Maj\+Tab.  
  
### Substituer la méthode OnMnemonic pour prendre en charge les mnémoniques  
 La gestion du clavier est presque terminée, mais il reste un problème à résoudre : les mnémoniques ne fonctionnent pas.  Si un utilisateur appuie sur Alt\+F, le focus ne saute pas à la zone d'édition « Prénom : ».  C'est pourquoi, vous substituez la méthode `OnMnemonic` :  
  
```  
virtual bool OnMnemonic(System::Windows::Interop::MSG% msg, ModifierKeys modifiers) override {  
    ::MSG m = ConvertMessage(msg);  
  
    // If it's one of our mnemonics, set focus to the appropriate hwnd  
    if (msg.message == WM_SYSCHAR && GetKeyState(VK_MENU /*alt*/)) {  
        int dialogitem = 9999;  
        switch (m.wParam) {  
            case 's': dialogitem = IDOK; break;  
            case 'c': dialogitem = IDCANCEL; break;  
            case 'f': dialogitem = IDC_EDIT1; break;  
            case 'l': dialogitem = IDC_EDIT2; break;  
            case 'p': dialogitem = IDC_EDIT3; break;  
            case 'a': dialogitem = IDC_EDIT4; break;  
            case 'i': dialogitem = IDC_EDIT5; break;  
            case 't': dialogitem = IDC_EDIT6; break;  
            case 'z': dialogitem = IDC_EDIT7; break;  
        }  
        if (dialogitem != 9999) {  
            HWND hwnd = GetDlgItem(dialog, dialogitem);  
            SetFocus(hwnd);  
            return true;  
        }  
    }  
    return false; // key unhandled  
};  
```  
  
 Pourquoi ne pas appeler `IsDialogMessage` dans ce cas précis ?  Vous vous heurtez au même problème qu'auparavant, à savoir que vous devez pouvoir indiquer au code [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] si votre code a géré ou non la séquence de touches, mais `IsDialogMessage` ne permet pas de le faire.  Il y a également un second problème car `IsDialogMessage` refuse de traiter le mnémonique lorsque le HWND doté du focus ne se trouve pas à l'intérieur de la boîte de dialogue.  
  
### Instancier la classe dérivée HwndHost  
 Pour finir, maintenant que la prise en charge des touches et de la tabulation est assurée, vous pouvez mettre votre <xref:System.Windows.Interop.HwndHost> dans l'application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] plus grande.  Si l'application principale est écrite en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], la façon la plus facile de la placer au bon endroit est de laisser un élément <xref:System.Windows.Controls.Border> vide là où vous souhaitez placer <xref:System.Windows.Interop.HwndHost>.  Vous créez ici un <xref:System.Windows.Controls.Border> appelé `insertHwndHostHere` :  
  
```  
<Window x:Class="WPFApplication1.Window1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    Title="Windows Presentation Framework Application"  
    Loaded="Window1_Loaded"  
    >  
    <StackPanel>  
        <Button Content="WPF button"/>  
        <Border Name="insertHwndHostHere" Height="200" Width="500"/>  
        <Button Content="WPF button"/>  
    </StackPanel>  
</Window>  
```  
  
 Il ne reste plus qu'à trouver un bon emplacement dans la séquence de code pour instancier le <xref:System.Windows.Interop.HwndHost> et le connecter au <xref:System.Windows.Controls.Border>.  Dans cet exemple, vous allez le mettre à l'intérieur du constructeur pour la classe dérivée <xref:System.Windows.Window> :  
  
```  
public partial class Window1 : Window {  
    public Window1() {  
    }  
  
    void Window1_Loaded(object sender, RoutedEventArgs e) {  
        HwndHost host = new ManagedCpp.MyHwndHost();  
        insertHwndHostHere.Child = host;  
    }  
}  
```  
  
 Ce qui nous donne :  
  
 ![Capture d'écran : application WPF](../../../../docs/framework/wpf/advanced/media/interoparch09.png "InteropArch09")  
  
## Voir aussi  
 [Interopérabilité WPF et Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)