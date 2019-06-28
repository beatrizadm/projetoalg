from tkinter import*
arquivo = open('Alunos.txt', 'r')
matriz = []
for linha in arquivo.readlines():
    linhas = linha.split(";")
    matriz.append(linhas)
for i in range(len(matriz)):
    matriz[i][-1] = matriz[i][-1].strip("\n")

listadamedia = []
for i in range(len(matriz)):
    media = (float(matriz[i][2]) + float(matriz[i][3]) + float(matriz[i][4]) + float(matriz[i][5])) / 4
    listadamedia.append("%.2f" % media)

listanomes = []
for k in range(len(matriz)):
    nomes = matriz[k][0]
    listanomes.append(nomes)

listafaltas = []
for w in range(len(matriz)):
    listafaltas.append(matriz[w][-1])

def panorama(): #1) Panorama geral: nome, matricula, situação
    string=''
    for i in range(len(matriz)):
        if int(matriz[i][-1])>=10:
            string+="Nome: "+matriz[i][0]+" | "+"Matrícula: "+matriz[i][1]+" | "+"Situação: "+"reprovado(a) por falta"+"\n"
        elif float(listadamedia[i])>7:
            string+="Nome: "+matriz[i][0]+" | "+"Matrícula: "+matriz[i][1]+" | "+"Situação: "+"aprovado(a)"+"\n"
        elif float(listadamedia[i])<7:
            string+="Nome: "+matriz[i][0]+" | "+"Matrícula: "+matriz[i][1]+" | "+"Situação: "+"reprovado(a)"+"\n"
    an = Tk()
    an['bg'] = 'black'
    end = Label(an, text=string, fg='white', bg='black',font='25')
    an.geometry('800x600')
    end.pack()
    an.mainloop()

def alunos(): #2) Alunos cadastrados na disciplina(nome e matricula)
    l = ''
    for linha in matriz:
        l += 'Nome: '+linha[0] + ' | ' + "Matrícula: "+linha[1] + '\n'
    an = Tk()
    an['bg'] = 'black'
    end = Label(an, text=l,fg='white',bg='black',font='25')
    an.geometry('800x600')
    end.pack()
    an.mainloop()

def reprovado(): #3) Reprovados: Listar o nome e a media dos alunos reprovados e porcentagem
    reprovado = []
    nomereprovado = []
    string=''
    for w in range(len(listadamedia)):
        if float(listadamedia[w])<7.00:
            reprovado.append(listadamedia[w])
            nomereprovado.append(listanomes[w])
    for p in range(len(reprovado)):
        string+='Nome: '+nomereprovado[p]+' | '+'Média: '+reprovado[p]+ '\n'
    porcentagem=(len(reprovado)*100)/len(listanomes)
    string+= 'Representa(m) '+"%.3f" % porcentagem + "%"+' de todos os alunos.'
    an = Tk()
    an['bg'] = 'black'
    end = Label(an, text=string, fg='white', bg='black', font='25')
    an.geometry('800x600')
    end.pack()
    an.mainloop()

def repfalt(): #4) Listar alunos que reprovaram por falta e sua porcentagem
    string=''
    cont=0
    for i in range(len(matriz)):
        if int(matriz[i][-1])>=10:
            cont+=1
            string+="Nome: "+matriz[i][0]+" | "+"Matrícula: "+matriz[i][1]+"\n"
    porcentagem=(cont*100)/len(listanomes)
    string+='Representa(m) '+"%.3f" % porcentagem + "%"+' de todos os alunos.'
    an = Tk()
    an['bg'] = 'black'
    end = Label(an, text=string, fg='white', bg='black', font='25')
    an.geometry('800x600')
    end.pack()
    an.mainloop()

def aprovados(): #5) Aprovados: Listar o nome e a média dos alunos aprovados e porcentagem
    aprovado = []
    nomeaprovado = []
    string = ''
    for w in range(len(listadamedia)):
        if float(listadamedia[w]) > 7.00:
            aprovado.append(listadamedia[w])
            nomeaprovado.append(listanomes[w])
    for p in range(len(aprovado)):
        string+='Nome: '+nomeaprovado[p]+' | '+'Média: '+aprovado[p]+ '\n'
    porcentagem = (len(aprovado) * 100) / len(listanomes)
    string+= 'Representa(m) '+"%.3f" % porcentagem + "%"+' de todos os alunos.'
    an = Tk()
    an['bg'] = 'black'
    end = Label(an, text=string, fg='white', bg='black', font='25')
    an.geometry('800x600')
    end.pack()
    an.mainloop()

def porcavacont():  #6 alunos aprovados por avaliação contínua e sua porcentagem
    string = ''
    quant = 0
    cont = 0
    for i in range(len(matriz)):
        quant += 1
        if (float(matriz[i][2]) + float(matriz[i][3]) + float(matriz[i][4])) / 4 >= 7:
            cont += 1
            string+="Nome: "+matriz[i][0]+" | "+"Matrícula: "+matriz[i][1]+"\n"
    porcentagem = (100*cont) / quant
    string+='Representa(m) '+"%.3f" % porcentagem + "%"+' de todos os alunos.'
    an = Tk()
    an['bg'] = 'black'
    end = Label(an, text=string, fg='white', bg='black', font='25')
    an.geometry('800x600')
    end.pack()
    an.mainloop()

def digitar(): #7) Local pra digitar a média mínima e máxima seguido dos alunos e suas médias que estejam nesse parâmetro e sua porcentagem
    minimo=float(push1.get())
    maximo=float(push2.get())
    parametromedia=[]
    nomeparametro=[]
    string = ''
    for w in range(len(listadamedia)):
        if float(listadamedia[w]) <= maximo and float(listadamedia[w]) >= minimo:
            parametromedia.append(listadamedia[w])
            nomeparametro.append(listanomes[w])
    for p in range(len(parametromedia)):
        string += 'Nome: '+ nomeparametro[p]+' | '+'Média: ' + parametromedia[p]+'\n'
    porcentagem = (len(parametromedia) * 100) / len(listadamedia)
    string += 'Representa(m) '+"%.3f" % porcentagem + "%"+' de todos os alunos.'
    title3['text'] = string

def notasentre():  #8 listar alunos que obtiveram nota entre x e y, sua nota e porcentagem
    cont, quant, aluno = 0, 0, ''
    nota1 = float(gof1.get())
    nota2 = float(gof2.get())
    x = int(gof3.get())
    for linha in matriz:
        quant += 1
        if nota1 <= float(linha[x+1]) <= nota2:
            cont += 1
            aluno += 'Aluno: '+ linha[0] + ' | ' + 'Nota: '+ str(round(float(linha[x+1]),1)) + '\n'
    porc = 'Representa(m) '+str(round((100 * cont) / quant, 3))+'%'+' de todos os alunos.'
    if porc == '0.0%':
        gow6['text']=('Não há alunos nessa faixa de notas na prova '+str(x)+'.')
    else:
        gow6['text']=(aluno + porc)

def search(): #9) Local para pesquisar os dados do aluno a partir da sua matrícula
    matricula = str(can1.get())
    dados = []
    for linha in matriz:
        if linha[1] == matricula:
            dados += linha
    lista = ['Nome: ', 'Matricula: ', 'Nota 1: ','Nota 2: ','Nota 3: ', 'Nota 4: ', 'Faltas: ']
    types = ''
    for each in range(len(dados)):
        types += lista[each]+dados[each]+'\n'
    letter['text'] = types

def mediaperiodo(): #10) Listar a media das notas no periodo
    soma=0
    string=''
    for i in range(len(listadamedia)):
        soma+=float(listadamedia[i])
    media=soma/(len(listadamedia))
    string+= "%.2f"%media
    an = Tk()
    an['bg'] = 'black'
    end = Label(an, text=string, fg='white', bg='black', font='25')
    an.geometry('800x600')
    end.pack()
    an.mainloop()

def mediaprova(): #11) Listar a média das notas por prova
    string=''
    quant = 0
    um = 0
    dois = 0
    tres = 0
    quatro = 0
    prova = int(endness.get())
    if prova >= 1 and prova <= 4 :
        for linha in matriz:
            quant += 1
            if prova == 1:
                um += float(linha[2])
            if prova == 2:
                dois += float(linha[3])
            if prova == 3:
                tres += float(linha[4])
            if prova == 4:
                quatro += float(linha[5])
        m1 = round(int(um)/quant, 1)
        m2 = round(int(dois)/quant, 1)
        m3 = round(int(tres)/quant, 1)
        m4 = round(int(quatro)/quant, 1)
        if prova == 1:
            string='Média da primeira prova: ' + str(m1)
        elif prova == 2:
            string='Média da segunda prova: ' + str(m2)
        elif prova == 3:
            string='Média da terceira prova: ' + str(m3)
        elif prova == 4:
            string='Média da quarta prova: ' + str(m4)



        endless['text'] = string
        endless['fg'] = 'white'
        endless['bg'] = 'black'
    else:
        endless['text'] = 'Escolha um número de 1 a 4!'
        endless['fg'] = 'red'
        endless['bg'] = 'black'


def reprovadofalta():  #12) Listar os alunos que passaram por media e reprovaram por falta e sua porcentagem
    string=''
    nomes = []
    medias = []
    faltas = []
    for w in range(len(listadamedia)):
        if float(listadamedia[w]) > 7.00:
            if int(listafaltas[w]) >= 10:
                nomes.append(listanomes[w])
                medias.append(listadamedia[w])
                faltas.append(listafaltas[w])
    for i in range(len(nomes)):
        string+='Nome: '+nomes[i]+' | '+'Média: '+medias[i]+' | '+'Faltas: '+faltas[i]+'\n'
    porcentagem = (len(nomes) * 100) / len(listanomes)
    string+='Representa(m) '+"%.3f" % porcentagem + "%"+' de todos os alunos.'
    an = Tk()
    an['bg'] = 'black'
    end = Label(an, text=string, fg='white', bg='black', font='25')
    an.geometry('800x600')
    end.pack()
    an.mainloop()

def withoutfalt(): #13) Listar alunos aprovados sem faltas e sua porcentagem
    string=''
    aluno = ''
    cont, quant = 0, 0
    for linha in matriz:
        quant += 1
        if ((float(linha[2]) + float(linha[3]) + float(linha[4]) + float(linha[5])) / 4) >= 7 and int(linha[-1]) == 0:
            aluno += linha[0] + '\n'
            cont += 1
    string += aluno
    porc = str(round((cont*100) / quant, 3))+'%'
    string += 'Representa(m) '+porc+' de todos os alunos.'
    an = Tk()
    an['bg'] = 'black'
    end = Label(an, text=string, fg='white', bg='black', font='25')
    an.geometry('800x600')
    end.pack()
    an.mainloop()

def brusco(): #14) Listar o nome dos alunos que tiveram bruscas diferencas de notas(6 pontos) e sua porcentagem
    string=''
    nome = []
    notas = []
    posicao = []
    for i in range(len(matriz)):
        if abs(float(matriz[i][2]) - float(matriz[i][3])) >= 6:
            nome.append(matriz[i][0])
            notas.append(matriz[i][2])
            notas.append(matriz[i][3])
            posicao.append(1)
            posicao.append(2)
        elif abs(float(matriz[i][2]) - float(matriz[i][4])) >= 6:
            nome.append(matriz[i][0])
            notas.append(matriz[i][2])
            notas.append(matriz[i][4])
            posicao.append(1)
            posicao.append(3)
        elif abs(float(matriz[i][2]) - float(matriz[i][5])) >= 6:
            nome.append(matriz[i][0])
            notas.append(matriz[i][2])
            notas.append(matriz[i][5])
            posicao.append(1)
            posicao.append(4)
        elif abs(float(matriz[i][3]) - float(matriz[i][4])) >= 6:
            nome.append(matriz[i][0])
            notas.append(matriz[i][3])
            notas.append(matriz[i][4])
            posicao.append(2)
            posicao.append(3)
        elif abs(float(matriz[i][3]) - float(matriz[i][5])) >= 6:
            nome.append(matriz[i][0])
            notas.append(matriz[i][3])
            notas.append(matriz[i][5])
            posicao.append(2)
            posicao.append(4)
        elif abs(float(matriz[i][4]) - float(matriz[i][5])) >= 6:
            nome.append(matriz[i][0])
            notas.append(matriz[i][4])
            notas.append(matriz[i][5])
            posicao.append(3)
            posicao.append(4)
    for w in range(len(nome)):
        string+="O aluno(a) "+ str(nome[w])+" obteve bruscas diferenças de notas durante as avaliações "+str(posicao[w])+" e "+str(posicao[w+1])+" com as respectivas notas: "+str(notas[w])+" e "+str(notas[w+1])+'\n'
    an = Tk()
    an['bg'] = 'black'
    end = Label(an, text=string, fg='white', bg='black', font='25')
    an.geometry('800x600')
    end.pack()
    an.mainloop()

# =============================================================================== #
# ~~~~~~~~~~~~~~~~~~~~~~~~~~ INTERFACE GRAFICA ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ #
# =============================================================================== #

def wind():
    global we, can1, sho1, letter
    we = Tk()
    we.title('wind')
    we['bg'] = 'black'
    can1 = Entry(we)

    coj = Label(we, text='Digite a matrícula do aluno: ',bg ='black',fg='white')
    coj.pack()
    can1.pack()
    sho1 = Button(we, text='Enviar', command=search)
    sho1.pack()
    letter = Label(we, text='',bg ='black',fg='white')
    letter.pack()
    we.geometry('800x600')
    we.mainloop()

def earth():
    global ea, gof1, gof2, gof3, gow6, gow5
    ea = Tk()
    gow1 = Label(ea, text='Nota x: ', font=('Arial','10'))
    gow1.place(x=150, y=100)
    gow2 = Label(ea, text='Nota y: ', font=('Arial','10'))
    gow2.place(x=150, y=150)
    gow3 = Label(ea, text='Prova z: ', font=('Arial','10'))
    gow3.place(x=150, y=200)
    gow4 = Label(ea, text='Avaliar alunos'+' que obtiveram nota'+'\n'+'entre x e y',fg='white',bg='black',font=('Arial','20','bold' ))
    gow4.grid(row=0, column=3)
    gow5 = Label(ea, text='', bg='black', fg='white')
    gow5.grid(row=1, column=4)
    gow6 = Label(ea, text='', bg='black', fg='white')
    gow6.grid(row=56, column=56)
    gof1 = Entry(ea, width=7)
    gof1.place(x=230, y=100)
    gof2 = Entry(ea, width=7)
    gof2.place(x=230, y=150)
    gof3 = Entry(ea, width=7)
    gof3.place(x=230, y=200)
    god1 = Button(ea, text='Enviar', command=notasentre)
    god1.place(x=230, y=300)
    ea['bg'] = 'black'
    ea.title('NotasEntrex&y')
    ea.geometry('800x600')
    ea.mainloop()

def pesquisa():
    global frase1
    inst = Tk()
    botao1 = Button(inst, text='Consultar média mínima e máxima no período',command=max, fg='white',bg='black',font='25')
    botao2 = Button(inst, text='Consultar nota mínima e nota máxima em uma das 4 provas',command=earth, fg='white',bg='black',font='25')
    botao3 = Button(inst, text='Consultar os dados do aluno pela matrícula',command=wind, fg='white',bg='black',font='25')
    frase1 = Label(inst,text='')
    botao1.pack(side=TOP, fill = BOTH, expand = 1)
    botao2.pack(side=TOP, fill = BOTH, expand = 1)
    botao3.pack(side=TOP, fill = BOTH, expand = 1)
    inst.geometry('800x600')
    inst.mainloop()

def especifico():
    global frase
    oi = Tk()
    botao1 = Button(oi, text='Alunos Aprovados por média',command=aprovados, fg='white',bg='black',font='25')  #5)
    botao2 = Button(oi, text='Alunos Aprovados por avaliação contínua',command=porcavacont, fg='white',bg='black',font='25')  #6)
    botao3 = Button(oi, text='Alunos Reprovados por média',command=reprovado, fg='white',bg='black',font='25')  #3)
    botao4 = Button(oi, text='Alunos Reprovados por falta',command=repfalt, fg='white',bg='black',font='25')  #4)
    frase = Label(oi, text='')
    botao1.pack(side=TOP, fill = BOTH, expand = 1)
    botao2.pack(side=TOP, fill = BOTH, expand = 1)
    botao3.pack(side=TOP, fill = BOTH, expand = 1)
    botao4.pack(side=TOP, fill = BOTH, expand = 1)
    oi.geometry('800x600')
    oi.mainloop()

def apurado():
    global frase
    iai = Tk()
    botao1 = Button(iai,text='Média das notas no período',command=mediaperiodo,fg='white',bg='black',font='25')  # 10)
    botao2 = Button(iai,text='Média das notas por prova',command=fire,fg='white',bg='black',font='25')  # 11)
    botao3 = Button(iai,text='Alunos Aprovados dos média e reprovados por falta',command=reprovadofalta,fg='white',bg='black',font='25')  # 12)
    botao4 = Button(iai,text='Alunos Aprovados sem faltas',command=withoutfalt,fg='white',bg='black',font='25')  # 13)
    botao5 = Button(iai,text='Alunos com bruscas diferenças de notas(6 pontos)',command=brusco,fg='white',bg='black',font='25')  # 14)
    frase = Label(iai, text='')
    botao1.pack(side=TOP, fill = BOTH, expand = 1)
    botao2.pack(side=TOP, fill = BOTH, expand = 1)
    botao3.pack(side=TOP, fill = BOTH, expand = 1)
    botao4.pack(side=TOP, fill = BOTH, expand = 1)
    botao5.pack(side=TOP, fill = BOTH, expand = 1)
    iai.geometry('800x600')
    iai.mainloop()
def fire():
    global endless, endness
    an = Tk()
    an['bg'] = 'black'
    end = Label(an, text='Insira qual prova você deseja obter a média', fg='white', bg='black', font='25')
    bolton = Button(an, text='Enviar', command=mediaprova)
    endness = Entry(an)
    endless = Label(an, text='', bg='black')
    an.geometry('800x600')
    end.pack()
    endness.pack()
    bolton.pack()
    endless.pack()
    an.mainloop()


def max():
    global push1, push2, title3
    mip = Tk()
    title1 = Label(mip, text='Insira a media mínima a ser pesquisada:',bg ='black',fg='white')
    title2 = Label(mip, text='Insira a media máxima a ser pesquisada:',bg ='black',fg='white')
    title3 = Label(mip, text='',bg='black',fg='white')
    push1 = Entry(mip)
    push2 = Entry(mip)
    mip['bg'] = 'black'
    putton1 = Button(mip, text='Enviar', command=digitar)
    title1.grid(row=0, column=0)
    title2.grid(row=1, column=0)
    push1.grid(row=0, column=1)
    push2.grid(row=1, column=1)
    putton1.grid(row=2, column=1)
    title3.place(x=380, y=10)
    mip.geometry('800x600')
    mip.mainloop()

def any():
    global end
    an = Tk()
    end = Label(an, text='')
    an.geometry('800x600')
    end.pack()
    an.mainloop()

def janela():
    global ent2
    f = Tk()
    f.title('janela')
    ent1 = Label(f, text='Clique em qual tarefa'+'\n'+'deseja realizar:',fg='white',bg='black', font=('Fixedsys','18'))
    ent1.pack()
    put2 = Button(f, text='Panorama geral', fg='white',bg='black',command=panorama,font=('25'))
    put2.pack(side=TOP, fill=BOTH, expand=1)
    put3 = Button(f, text='Alunos cadastrados', fg='white',bg='black',command=alunos,font=('25'))
    put3.pack(side=TOP, fill=BOTH, expand=1)
    put1 = Button(f, text='Dados específicos', fg='white',bg='black',command=especifico,font=('25'))
    put1.pack(side=TOP, fill=BOTH, expand=1)
    put4 = Button(f, text='Local para pesquisa', fg='white',bg='black', command=pesquisa,font=('25'))
    put4.pack(side=TOP, fill=BOTH, expand=1)
    put5 = Button(f, text='Apurado do período', fg='white',bg='black',command=apurado,font=('25'))
    put5.pack(side=TOP, fill=BOTH, expand=1)
    f.geometry('800x600')
    f['bg']='black'
    f.mainloop()

i = Tk()
i.title('Avaliação dados alunos')
i['bg'] = 'black'
texto1 = Label(i, text='AVALIAÇÃO ESTATÍSTICA DE ALUNOS',fg='white', bg = 'black',font=('System','30','bold'))
texto1.place(x=35, y=120)
input1 = Entry(i, width=5)
input2 = Entry(i, width=5)
input3 = Entry(i, width=5)
botao1 = Button(i, text='CLIQUE PARA ENTRAR',font=('Verdana','10','bold'),fg='white',bg='black', width = 22, height=10, command=janela)
botao1.place(x=300,y=250)
i.geometry('800x600')
i.mainloop()
