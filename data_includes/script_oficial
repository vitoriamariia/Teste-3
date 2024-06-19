PennController.ResetPrefix(null);
PennController.DebugOff();

Sequence("Participantes", "Instrucoes", "Experimento1", "Experimento2", "Final", SendResults());

Header(
  defaultText
    .css("font-size", "1.2em")
    .print(),
  defaultTextInput
    .css("font-size", "1.2em")
    .print(),
  defaultButton
    .css("font-size", "1.2em")
    .print()
    .center()
    .wait()
);

newTrial("Participantes",
  newText("<p>Ola! Seja bem-vindo ao nosso experimento!</p>")
    .print(),
  newText("<p>Por gentileza, escreva o SEU NOME COMPLETO NA CAIXA ABAIXO</p>")
    .print(),
  newTextInput("SeuNome")
    .print()
    .log(),
  newText("<p>Por gentileza, selecione o CURSO que faz na UFERSA</p>")
    .print(),
  newDropDown("curso", "Selecione seu curso")
    .add("Engenharia", "Ciencias e Tecnologias", "Letras")
    .css("font-size", "1.2em")
    .print()
    .log(),
  newButton("Vamos para as instrucoes")
    .print()
    .wait(),
  newVar("NOME")
    .global()
    .set(getTextInput("SeuNome"))
)
.log("NOME", getVar("NOME"));

newTrial("Instrucoes",
  newText("<p>Leia com atenção:</p>")
    .print(),
  newText("<p>Leia a situação fictícia e leia em voz alta a frase em destaque</p>")
    .print(),
  newButton("Iniciar")
    .print()
    .wait()
);

newTrial("Experimento1",
Template("teste_auditivo.csv",
  row => newTrial("Experimento1",
    newAudio("AudioExperimento", row.AudioExperimento)
      .play(),
    newImage("alto_falante_icone.png")
      .size(90, 90)
      .print()
      .center(),
    newButton("Próximo")
      .log()
      .wait()
      .remove(),
    getImage("alto_falante_icone.png")
      .remove(),
    newText("A", row.SentencaA)
      .print(),
    newText("B", row.SentencaB)
      .print(),
    newCanvas("canvas", 1000, 500)
      .add(250, 250, getText("A"))
      .add(750, 250, getText("B"))
      .print(),
    newSelector()
      .add(getText("A"), getText("B"))
      .keys("A", "B")
      .log()
      .wait()
  ))
  .log("Group", row.Group)
  .log("Item", row.Item)
);

newTrial("Experimento2",
  newText("Imagine a seguinte situação: você encontra uma receita de macarrão gourmet no TikTok e resolve recriar essa receita. Suponha que você seguiu a receita à risca, com todos os seus passos. Ao final, prova e gosta muito. Você, então, diz:")
    .print(),
  newText("Ficou muito gostoso, o macarrão")
    .css("font-weight", "bold")
    .print(),
  newButton("Próximo")
    .print()
    .wait()
);

newTrial("Final",
  newText("Obrigada por participar do experimento!")
    .print(),
  newButton("Finalizar")
    .print()
    .wait()
)
.setOption("countsForProgressBar", false);
