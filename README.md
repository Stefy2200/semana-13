# semana-13
import tkinter as tk
from tkinter import messagebox

def mostrar_mensaje():
    messagebox.showinfo("Mensaje", "Hola, esto es un mensaje de prueba.")

# Crear la ventana principal
ventana = tk.Tk()
ventana.title("Ejemplo de GUI con Tkinter")
ventana.geometry('400x400')

# Crear un botón
boton = tk.Button(ventana, text="Mostrar mensaje", command=mostrar_mensaje)
boton.pack(pady=20)

# Ejecutar el bucle de eventos
ventana.mainloop()
import tkinter as tk
from tkinter import messagebox

def calcular_resultado():
    try:
        # Obtiene el valor del campo de entrada y realiza un cálculo
        numero = float(entrada.get())
        resultado = numero * 2
        # Muestra el resultado en el área de texto
        area_texto.insert(tk.END, f"El doble de {numero} es {resultado}\n")
    except ValueError:
        messagebox.showerror("Error", "Por favor, introduce un número válido.")

# Función para limpiar el área de texto
def limpiar_resultado():
    area_texto.delete(1.0, tk.END)

# Crear la ventana principal
ventana = tk.Tk()
ventana.title("Software de Cálculo del Doble")
ventana.geometry("400x400")

# Crear un menú
barra_menu = tk.Menu(ventana)
ventana.config(menu=barra_menu)

# Crear una opción de menú "Archivo" con una opción "Salir"
menu_archivo = tk.Menu(barra_menu)
barra_menu.add_cascade(label="Archivo", menu=menu_archivo)
menu_archivo.add_command(label="Salir", command=ventana.quit)

# Crear un título
titulo = tk.Label(ventana, text="Calcula el doble de un número")
titulo.pack(pady=10)

# Crear una etiqueta
etiqueta = tk.Label(ventana, text="Introduce un número:")
etiqueta.pack()

# Crear un campo de entrada
entrada = tk.Entry(ventana)
entrada.pack()

# Crear un botón para calcular el resultado
boton_calcular = tk.Button(ventana, text="Calcular", command=calcular_resultado)
boton_calcular.pack(pady=5)

# Crear un botón para limpiar el resultado
boton_limpiar = tk.Button(ventana, text="Limpiar", command=limpiar_resultado)
boton_limpiar.pack(pady=5)

# Crear un área de texto para mostrar el resultado
area_texto = tk.Text(ventana, height=10, width=30)
area_texto.pack()

# Ejecutar el bucle de eventos
ventana.mainloop()
import tkinter as tk

def agregar_caracter(caracter):
    entrada.insert(tk.END, caracter)

def calcular(*args):
    try:
        expresion = entrada.get()
        resultado = eval(expresion)
        entrada.delete(0, tk.END)
        entrada.insert(tk.END, str(resultado))
        log.config(text=f"Operación: {expresion}, Resultado: {resultado}")
    except Exception as e:
        entrada.delete(0, tk.END)
        entrada.insert(tk.END, "Error")
        log.config(text="Error")

def limpiar():
    entrada.delete(0, tk.END)
    log.config(text="")

def salir():
    ventana.quit()

# Crear la ventana principal
ventana = tk.Tk()
ventana.title("Calculadora")
ventana.geometry("300x300")

# Centrar la ventana en la pantalla
ancho_ventana = ventana.winfo_reqwidth()
alto_ventana = ventana.winfo_reqheight()
posicion_derecha = int(ventana.winfo_screenwidth() / 2 - ancho_ventana / 2)
posicion_abajo = int(ventana.winfo_screenheight() / 2 - alto_ventana / 2)
ventana.geometry("+{}+{}".format(posicion_derecha, posicion_abajo))

# Crear un menú
barra_menu = tk.Menu(ventana)
ventana.config(menu=barra_menu)

menu_archivo = tk.Menu(barra_menu)
barra_menu.add_cascade(label="Archivo", menu=menu_archivo)
menu_archivo.add_command(label="Limpiar", command=limpiar)
menu_archivo.add_separator()
menu_archivo.add_command(label="Salir", command=salir)

# Crear un campo de entrada
entrada = tk.Entry(ventana, font=("Arial", 18), justify="right")
entrada.grid(row=0, column=0, columnspan=4, padx=10, pady=10)
entrada.bind("<Return>", calcular)
entrada.bind("<Escape>", lambda event: limpiar())

# Crear un label para visualizar las operaciones en formato de log
log = tk.Label(ventana, text="", font=("Arial", 12))
log.grid(row=1, column=0, columnspan=4, padx=10, pady=5)

# Crear los botones de los números
numeros = "7894561230"
for i, num in enumerate(numeros):
    tk.Button(ventana, text=num, font=("Arial", 14), command=lambda num=num: agregar_caracter(num)).grid(row=(i//3)+2, column=(i%3), padx=5, pady=5)

# Botón para el punto decimal
tk.Button(ventana, text=".", font=("Arial", 14), command=lambda: agregar_caracter(".")).grid(row=5, column=1, padx=5, pady=5)

# Botón para el cálculo
tk.Button(ventana, text="=", font=("Arial", 14), command=calcular).grid(row=5, column=0, columnspan=2, padx=5, pady=5)

# Crear los botones de las operaciones
operadores = ["+", "-", "*", "/"]
for i, operador in enumerate(operadores):
    tk.Button(ventana, text=operador, font=("Arial", 14), command=lambda op=operador: agregar_caracter(op)).grid(row=i+2, column=3, padx=5, pady=5)

# Ejecutar el bucle de eventos
ventana.mainloop()
