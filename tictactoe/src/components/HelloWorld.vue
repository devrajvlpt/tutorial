<template>
<div class="ml-40 mt-32">
  <h1>TIC TAC TOE</h1>
  <div class="flex flex-wrap h-4">
    <div class="w-1/3 p-2 border px-4 py-8 hover:bg-gray-400" v-for="(square, index) in board" :key=index v-on:click="markChar(index)">
      <span class="text-bold font-xl">{{square}}</span>
    </div>
  </div>
</div>
    
</template>

<script>
export default {
  data(){
      return{
          board:["", "", "", "", "", "", "", "", ""],
          player_turn: "X"
      }
      
    
  },
  methods:{
    markChar(index){
      let player_turn =  this.player_turn
      let board = this.board
      //  check winning on the board define winning combos
      let winning_combos = [
        [0, 1, 2],
        [3, 4, 5],
        [6, 7, 8],
        [0, 4, 8],
        [2, 4, 6],
        [1, 4, 7],
        [0, 3, 6],
        [2, 5, 8]
      ]
      board[index] = player_turn
      
      for (let i =0; i<winning_combos.length; i++){
          let winning_row =  winning_combos[i];
          // console.log(winning_row);
          
          let p1 = winning_row[0]
          let p2 = winning_row[1]
          let p3 = winning_row[2]
          
          if (board[p1] == board[p2] && board[p2] == board[p3] && board[p3] == board[p1] && board[p1] != "" && board[p2] !="" && board[p3] !=""){
            alert("Winning combo,")
          }
      }
      console.log(board)
      player_turn = ( player_turn == "X" ) ? "O" : "X"
      this.$set(board, board)
      this.player_turn = player_turn

    }
  }
}
</script>
