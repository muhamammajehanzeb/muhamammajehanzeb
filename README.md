- 👋 Hi, I’m @muhamammajehanzeb
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
import 'dart:async';
import 'package:flutter/material.dart';
import 'package:flutter/services.dart';
import 'package:flutter_svg/svg.dart';
import 'package:google_fonts/google_fonts.dart';
import 'package:quran_app/globals.dart';
import 'package:quran_app/models/surah.dart';
import 'package:quran_app/screens/detail_screen.dart';


class SurahTab extends StatelessWidget {
  const SurahTab({super.key});

  
  Future<List<Surah>> _getSurahList() async {
    
     String data = await rootBundle.loadString('assets/datas/list-surah.json');
     List<Surah> surahlist =[];
    return surahFromJson(data);
  }

  @override
  Widget build(BuildContext context) {
    return FutureBuilder<List<Surah>>(
      future: _getSurahList() ,
      initialData: [],
       builder:((context,snapshot) {
        if(!snapshot.hasData){
          return  Container();
        }
        return ListView.separated(
          itemBuilder: (context, index)=>_surahItem(surah: snapshot.data!.elementAt(index)),
           separatorBuilder:(context,index)=>Container(),
            itemCount: snapshot.data!.length);
       }) );
  }

  Container _surahItem({required Surah surah}) => Container(
    child: Text('Ok',style: GoogleFonts.poppins(color: Colors.white),),
  );
}



