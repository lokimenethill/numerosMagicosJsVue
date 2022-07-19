<template>
  <v-row justify="center" align="center">
    <v-col >
        <h1>Cuadros Mágicos</h1>
        <v-alert
      color="#C51162"
      dark
      icon="mdi-material-design"
      border="right"
    >
       Resolucion de cuadro Magico para n*n par ejemplo de 4*4
    </v-alert>
       
      Datos de entrada:
        {{datos}}
        <v-alert
        v-if="estado==true"
      dense
      type="info"
    >
      <h1>El Cuadro es Mágico!!!</h1>
    </v-alert>
        <table>
            <tr >
                <td>
                    
                </td>
                <td>
                   
                </td>
                <td>
                   
                </td>
                <td>
                    
                </td>
                <td>
                    Resultado de filas
                    <p>
                        {{diagonal2}}
                    </p>
                </td>
            </tr>
            <tr >
                <td>
                    <v-text-field v-model="datos.f1[0].c1" outlined></v-text-field>
                </td>
                <td>
                    <v-text-field v-model="datos.f1[0].c2" outlined></v-text-field>
                </td>
                <td>
                    <v-text-field v-model="datos.f1[0].c3" outlined></v-text-field>
                </td>
                <td>
                    <v-text-field v-model="datos.f1[0].c4" outlined></v-text-field>
                </td>
                <td>
                    <v-text-field :value="sumaF1" single-line readonly></v-text-field>
                </td>
            </tr>
             <tr >
                <td>
                    <v-text-field v-model="datos.f2[0].c1" outlined></v-text-field>
                </td>
                <td>
                    <v-text-field v-model="datos.f2[0].c2" outlined></v-text-field>
                </td>
                <td>
                    <v-text-field v-model="datos.f2[0].c3" outlined></v-text-field>
                </td>
                <td>
                    <v-text-field v-model="datos.f2[0].c4" outlined></v-text-field>
                </td>
                <td>
                    <v-text-field :value="sumaF2" single-line readonly></v-text-field>
                </td>
            </tr>
             <tr >
                <td>
                    <v-text-field v-model="datos.f3[0].c1" outlined></v-text-field>
                </td>
                <td>
                    <v-text-field v-model="datos.f3[0].c2" outlined></v-text-field>
                </td>
                <td>
                    <v-text-field v-model="datos.f3[0].c3" outlined></v-text-field>
                </td>
                <td>
                    <v-text-field v-model="datos.f3[0].c4" outlined></v-text-field>
                </td>
                <td>
                    <v-text-field :value="sumaF3" single-line readonly></v-text-field>
                </td>
            </tr>
             <tr >
                <td>
                    <v-text-field v-model="datos.f4[0].c1" outlined></v-text-field>
                </td>
                <td>
                    <v-text-field v-model="datos.f4[0].c2" outlined></v-text-field>
                </td>
                <td>
                    <v-text-field v-model="datos.f4[0].c3" outlined></v-text-field>
                </td>
                <td>
                    <v-text-field v-model="datos.f4[0].c4" outlined></v-text-field>
                </td>
                <td>
                    <v-text-field :value="sumaF4" single-line readonly></v-text-field>
                </td>
            </tr>
        </table>
        <v-alert
      color="primary"
      dark
      border="left"
      prominent
    >
      <p>Numero Magico = {{sumatoria}}/4 = {{numeroMagico}}</p>
        Resultado de columnas
    </v-alert>
        
        <table>
            <tr>
                <td>
                    <v-text-field :value="sumaC1" single-line readonly></v-text-field>
                </td>
                <td>
                    <v-text-field :value="sumaC2" single-line readonly></v-text-field>
                </td>
                <td>
                    <v-text-field :value="sumaC3" single-line readonly></v-text-field>
                </td>
                <td>
                    <v-text-field :value="sumaC4" single-line readonly></v-text-field>
                </td>
                <td>
                    <v-text-field :value="diagonal1" single-line readonly></v-text-field>
                </td>
            </tr>
        </table>
         <v-btn
         @click="resolver()"
        class="ma-2"
        color="primary"
        dark
      >
        Resolver
        <v-icon
          dark
          right
        >
          mdi-checkbox-marked-circle
        </v-icon>
      </v-btn>
    </v-col>
  </v-row>
</template>

<script>
import { computed } from 'vue'
export default {
  name: 'IndexPage'
  ,
data(){
    return{
        datos:{
            f1:[{c1:1,c2:2,c3:3,c4:4}],
            f2:[{c1:5,c2:6,c3:7,c4:8}],
            f3:[{c1:9,c2:10,c3:11,c4:12}],
            f4:[{c1:13,c2:14,c3:15,c4:16}],
        },
        estado:false
    }
},
computed:{
    sumaC1(){
        let r=0;
        for(let i=1;i<5;i++){
        r=r+parseInt(this.datos[`f${i}`][0].c1);
        }
        return r;
    },
    sumaC2(){
        let r=0;
        for(let i=1;i<5;i++){
        r=r+parseInt(this.datos[`f${i}`][0].c2);
        }
        return r;
    },
    sumaC3(){
        let r=0;
        for(let i=1;i<5;i++){
        r=r+parseInt(this.datos[`f${i}`][0].c3);
        }
        return r;
    },
    sumaC4(){
        let r=0;
        for(let i=1;i<5;i++){
        r=r+parseInt(this.datos[`f${i}`][0].c4);
        }
        return r;
    },
    sumaF1(){
        let r=0;
        for(let i=1;i<5;i++){
        r=r+parseInt(this.datos.f1[0][`c${i}`]);
        }
        return r;
    },
    sumaF2(){
        let r=0;
        for(let i=1;i<5;i++){
        r=r+parseInt(this.datos.f2[0][`c${i}`]);
        }
        return r;
    },
    sumaF3(){
        let r=0;
        for(let i=1;i<5;i++){
        r=r+parseInt(this.datos.f3[0][`c${i}`]);
        }
        return r;
    },
    sumaF4(){
        let r=0;
        for(let i=1;i<5;i++){
        r=r+parseInt(this.datos.f4[0][`c${i}`]);
        }
        return r;
    },
    diagonal1(){
        let r=0;
        for(let i=1;i<5;i++){
        r=r+parseInt(this.datos[`f${i}`][0][`c${i}`]);
        }
        return r;
    },
    diagonal2(){
        let r=0;
        let j=4;
        for(let i=1;i<5;i++){
        r=r+parseInt(this.datos[`f${i}`][0][`c${j}`]);
        j--;
        }
        return r;
    },
    numeroMagico(){
        let sumatoria = 0;
        for(let i=1;i<5;i++){
            for(let j=1;j<5;j++){
                sumatoria=sumatoria+parseInt(this.datos[`f${i}`][0][`c${j}`]);
            }
        }
        return sumatoria/4;
    },
    sumatoria(){
        let sumatoria = 0;
        for(let i=1;i<5;i++){
            for(let j=1;j<5;j++){
                sumatoria=sumatoria+parseInt(this.datos[`f${i}`][0][`c${j}`]);
            }
        }
        return sumatoria;
    },
    wData(){
        let watcher = this.sumaC1+this.sumaC2+this.sumaC3+this.sumaC4;
        return watcher;
    }
},
methods:{
    resolver(){
        let cambios =0;
        let val = 0;
        let valTmp = 0;
        let pos1=1;
        let pos2=4;
        //casos donde el valor de la fila es igual al de la columna
        while(cambios<2){
            val = parseInt(this.datos[`f${pos2}`][0][`c${pos2}`]);
            valTmp = parseInt(this.datos[`f${pos1}`][0][`c${pos1}`]);
            //alert(`val : ${val} valtmp: ${valTmp}`)
            if(val>valTmp){
                this.datos[`f${pos1}`][0][`c${pos1}`]=val
                this.datos[`f${pos2}`][0][`c${pos2}`]=valTmp
                //alert(`val : ${val} > valtmp: ${valTmp}`)
            }
            pos1++;
            pos2--;
            cambios++;
        }
        cambios=0;
        pos1=1;
        pos2=4;
        //casos donde la fila es diferente de la columna
        while(cambios<2){
            val = parseInt(this.datos[`f${pos1}`][0][`c${pos2}`]);
            valTmp = parseInt(this.datos[`f${pos2}`][0][`c${pos1}`]);
            //alert(`val : ${val} valtmp: ${valTmp}`)
            if(val<valTmp){
                this.datos[`f${pos2}`][0][`c${pos1}`]=val
                this.datos[`f${pos1}`][0][`c${pos2}`]=valTmp
                //alert(`val : ${val} > valtmp: ${valTmp}`)
            }
            pos1++;
            pos2--;
            cambios++;
        }
        if(this.sumaC1==this.numeroMagico&&this.sumaC2==this.numeroMagico&&this.sumaC3==this.numeroMagico&&this.sumaC4==this.numeroMagico&&this.sumaF1==this.numeroMagico&&this.sumaF2==this.numeroMagico&&this.sumaF3==this.numeroMagico&&this.sumaF4==this.numeroMagico&&this.diagonal1==this.numeroMagico&&this.diagonal2==this.numeroMagico){
            this.estado = true;
        }else{
            this.estado = false;
        }
    },
},
watch:{
    wData(){
        if(this.sumaC1==this.numeroMagico&&this.sumaC2==this.numeroMagico&&this.sumaC3==this.numeroMagico&&this.sumaC4==this.numeroMagico&&this.sumaF1==this.numeroMagico&&this.sumaF2==this.numeroMagico&&this.sumaF3==this.numeroMagico&&this.sumaF4==this.numeroMagico&&this.diagonal1==this.numeroMagico&&this.diagonal2==this.numeroMagico){
            this.estado = true;
        }else{
            this.estado = false;
        }
    }
}

}
</script>
