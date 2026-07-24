import 'package:flutter/material.dart;
import 'package:flutter_tts/flutter_tts.dart;
import 'package:speech_to_text/speech_to_text.dart';

voidmain(){ 
runapp(const myapp());
}

class myapp extends statelesswidget{ 
const myapp({super.key});
@override
widget build(buildcontext) {
return materialapp(
debugshowcheckedmodebanner. false,
home:voiceAssistant();
   );
  }
 }
 class voiceAssistant extends statefulwidget {
 @override
 state<voiceAssistant> createstate()=>_voiceAssistantstate();
 } 

 class_voiceAssistantstate extends state<voiceAssistant>{

 final speechtotext speech = speechToText();
 final flutterTtstts=flutterTts();
  string text ="pressMic";

  @override
  void initstate() {
   super.initstate();
   initspeech();
   }

  void initspeech()async{
  await speech.initalize();
  await tts.setlanguage("en-us");
  }

  void listen() async {
  if (!speech.islistening){
   await speech.listen(onResult: (result){
   setstate((){
    text=resultrecognizedwords;
    });

    command(result.recognizewords.toLowercase();
    });
    } else {
    speech.stop();
     }
    }

    void speak(stringmsg) async{
    await tts.speak(msg);
    }

    void command(string cmb){
    if(cmd.contains("hello")){
      speak("Hello, Iam Signal Ai.);
      }elseif(cmb.contains("time")){
       speak(datetime.now().tostring());
      }elseif(cmb.contains("name")){
       speak("My name is signsl Ai.");
      }else{
       speak("sorry I dont understand.");
       }
       }

       @override
       Widgetbuild(buildcontext context){
       return scafold(
        appBar:AppBar(title:const text("Signal Voice Assistant"));
         body:centre(
         child:text(
         text,
         style:const textstyle(fontsize: 22),
         ), 
        ),
        floatingActionButton:FloatingActingButton(
          onPressed: listen,
          child: const Icon(icons.mic),
           ),
          );
         }
       }  
      
    
  








  
  
 
 


 
