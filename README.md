# Graphical-User-Interface


Aplikasi GUI untuk memperbaiki noise pada gambar dengan metode median filter (Graphical User Interface)

~~~
Nama  : Fachmi Eka Pangestu
NIM   : 311810084
Kelas : TI 18 D5
~~~
# 1. Tutorial Cara Membuat Applikasi GUI
ketik guide pada command windows lalu tekan enter

![image](https://user-images.githubusercontent.com/43899437/165760596-1e270d44-4020-4898-a4f8-8cea7cd5ce5f.png)

# 2. Creat New GUI
Pilih creat new GUI, tentukan lokasi penyimpanan lalu tekan OK

![image](https://user-images.githubusercontent.com/43899437/165761015-177ca967-de7e-4ffc-a579-2bb700ecd9f0.png)

# 3. Buat Tampilan GUI sesuai yang di inginkan
![image](https://user-images.githubusercontent.com/43899437/165761449-548c0d36-042c-4460-9c86-066831d07206.png)

# 4. Buat Source Code
Untuk memanggil tombol fungsi pada source klik kanan pada tombol fungsi >> view callback >> callback

![image](https://user-images.githubusercontent.com/43899437/165761697-a63fa579-1e9a-413f-ba5f-7de3ea04e65d.png)

Membuat Source Code
~~~
function varargout = UTS(varargin)
% UTS MATLAB code for UTS.fig
%      UTS, by itself, creates a new UTS or raises the existing
%      singleton*.
%
%      H = UTS returns the handle to a new UTS or the handle to
%      the existing singleton*.
%
%      UTS('CALLBACK',hObject,eventData,handles,...) calls the local
%      function named CALLBACK in UTS.M with the given input arguments.
%
%      UTS('Property','Value',...) creates a new UTS or raises the
%      existing singleton*.  Starting from the left, property value pairs are
%      applied to the GUI before UTS_OpeningFcn gets called.  An
%      unrecognized property name or invalid value makes property application
%      stop.  All inputs are passed to UTS_OpeningFcn via varargin.
%
%      *See GUI Options on GUIDE's Tools menu.  Choose "GUI allows only one
%      instance to run (singleton)".
%
% See also: GUIDE, GUIDATA, GUIHANDLES

% Edit the above text to modify the response to help UTS

% Last Modified by GUIDE v2.5 27-Apr-2022 05:56:59

% Begin initialization code - DO NOT EDIT
gui_Singleton = 1;
gui_State = struct('gui_Name',       mfilename, ...
                   'gui_Singleton',  gui_Singleton, ...
                   'gui_OpeningFcn', @UTS_OpeningFcn, ...
                   'gui_OutputFcn',  @UTS_OutputFcn, ...
                   'gui_LayoutFcn',  [] , ...
                   'gui_Callback',   []);
if nargin && ischar(varargin{1})
    gui_State.gui_Callback = str2func(varargin{1});
end

if nargout
    [varargout{1:nargout}] = gui_mainfcn(gui_State, varargin{:});
else
    gui_mainfcn(gui_State, varargin{:});
end
% End initialization code - DO NOT EDIT


% --- Executes just before UTS is made visible.
function UTS_OpeningFcn(hObject, eventdata, handles, varargin)
% This function has no output args, see OutputFcn.
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
% varargin   command line arguments to UTS (see VARARGIN)

% Choose default command line output for UTS
handles.output = hObject;

% Update handles structure
guidata(hObject, handles);

% UIWAIT makes UTS wait for user response (see UIRESUME)
% uiwait(handles.figure1);


% --- Outputs from this function are returned to the command line.
function varargout = UTS_OutputFcn(hObject, eventdata, handles) 
% varargout  cell array for returning output args (see VARARGOUT);
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Get default command line output from handles structure
varargout{1} = handles.output;


% --- Executes on button press in pushbutton1.
function pushbutton1_Callback(hObject, eventdata, handles)
% hObject    handle to pushbutton1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
[filename, pathname] = uigetfile({'*.jpg','*.png'});

citra1 = imread ([pathname, filename]);
%menampilkan di axes
axes(handles.axes1);
imshow(citra1);
[tinggiA, lebarA] = size(citra1);

%proses filter median untuk citra mobil
for baris=2 : tinggiA-1
    for kolom=2 : lebarA-1
        dataA = [citra1(baris-1, kolom-1) citra1(baris-1, kolom) citra1(baris-1, kolom+1)  ...
              citra1(baris, kolom-1) citra1(baris, kolom) citra1(baris, kolom+1)  ...
              citra1(baris+1, kolom-1) citra1(baris+1, kolom) citra1(baris+1, kolom+1)];
        
        % Urutkan
        for i=1 : 8
            for j=i+1 : 9
                if dataA(i) > dataA(j)
                    tmpA = dataA(i);
                    dataA(i) = dataA(j);
                    dataA(j) = tmpA;
                end
            end
        end 
        
        % Ambil nilai median
        citra2(baris, kolom) = dataA(5);
    end
end

%menampilkan di axes2
axes(handles.axes2);
imshow(citra2);
~~~
![image](https://user-images.githubusercontent.com/43899437/165762090-9cbba1a5-99c4-413e-8e0c-bac4db19e895.png)

# 5. Running Aplikasi GUI
![gui](https://user-images.githubusercontent.com/43899437/165762621-41d49099-0fa9-4e92-994c-4731a9efae1b.png)

# 6. Input Gambar
![gui](https://user-images.githubusercontent.com/43899437/165763051-3948c724-419d-4333-aad5-78df9477b1c6.png)

![image](https://user-images.githubusercontent.com/43899437/165763904-de52bb43-d15c-47c5-ae1e-067cb1a26ef6.png)

# 7. Hasil Akhir
![image](https://user-images.githubusercontent.com/43899437/165764086-95c6751f-6619-4b27-a1c3-52fe55237b53.png)



