<template>
   <div class="center-vertical" id="join-room">
        <div class="join-room-header centering-content">
            <span>Join your friends here!</span>
        </div>
        <div class="join-room-roomcode center-vertical">
            <span>Room Code</span>
            <input id="roomcode-input" type="text" tabindex="1" v-model="roomId">
            <div class="item-input-error-message">
              <p v-if="!$v.roomId.required">This field is required!</p>
              <p v-if="!$v.roomId.minLength || !$v.roomId.maxLength">This field must be exactly 5 characters!</p>
              <p v-if="!$v.roomId.alphaNum">This field must contain only alphanumeric characters!</p>
            </div>
        </div>
        <div class="join-room-usercode center-vertical">
            <span>Display name (&lt;12 characters)</span>
            <input id="usercode-input" type="text" tabindex="2" v-model="playerName">
            <div class="item-input-error-message">
              <p v-if="!$v.playerName.required">This field is required!</p>
              <p v-if="!$v.playerName.maxLength">This field must be less than 12 characters!</p>
              <p v-if="!$v.playerName.alphaNum">This field must contain only alphanumeric characters!</p>
            </div>
        </div>

        <div class="disclaimer center-vertical" v-if="!$v.$invalid">
            <span>By clicking PLAY, you are agreeing</span>
            <span>to our <a href="#">Terms of Service.</a></span>
        </div>

        <img id="join-room-join" src="@/assets/join-room/button_join.png" tabindex="3" v-on:click="goToConfirmInGame" v-if="!$v.$invalid">

    </div>
</template>

<style lang="scss" scoped>
#join-room {
  overflow-y: hidden;
}
.join-room-header {
  font-size: 40px;
  text-align: center;
}
.join-room-roomcode {
  align-items: flex-start;
  margin-top: 10%;
  font-size: 20px;

  #roomcode-input {
    font-family: Fredoka, serif;
    font-size: 30px;
    color: #e13d61;
    margin-top: 5%;
    background-color: transparent;
    border: none;
    border-bottom: 2px solid #d8d8d8;
    width: 100%;
  }

  #roomcode-input:focus {
    border: none;
    border-bottom: 2px solid #e13d61;
  }
}
.join-room-usercode {
  align-items: flex-start;
  margin-top: 8%;
  font-size: 20px;

  #usercode-input {
    font-family: Fredoka, serif;
    font-size: 30px;
    color: #e13d61;
    margin-top: 5%;
    background-color: transparent;
    border: none;
    border-bottom: 2px solid #f51c1c;
    width: 100%;
  }

  #usercode-input:focus {
    border: none;
    border-bottom: 2px solid #e13d61;
  }
}

#join-room-join {
  margin-top: 40px;
  max-width: 80%;
}

.item-input-error-message {
  color: #e13d61;
  font-size: 15px;
  text-align: center;
}

.disclaimer {
  align-items: center;
  font-size: 0.8em;
  margin-top: 10%;
}
</style>

<script>
import { required, alphaNum, minLength, maxLength } from 'vuelidate/lib/validators'

export default {
  methods: {
    goToConfirmInGame: function(event) {
      this.$router.push('confirm-in-game')
    },
    validateRoomCode: function() {
      console.log("validateRoomCode")
    },
    validatePlayerName: function() {
      console.log("validatePlayerName")
    }
  },
  computed: {
    roomId: {
      get() { return this.$store.state.roomId },
      set(value) { this.$store.commit('updateRoomId', value) }
    },
    playerName: {
      get() { return this.$store.state.playerName },
      set(value) { this.$store.commit('updatePlayerName', value) }
    }
  },
  validations: {
    roomId : {
      required,
      alphaNum,
      minLength: minLength(5),
      maxLength: maxLength(5)
    },
    playerName : {
      required,
      alphaNum,
      maxLength: maxLength(12)
    }
  }
}
</script>
