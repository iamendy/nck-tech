<template>
  <!--=====Payment Starts Here=====-->
  <section id="payment-details">
    <div class="container">
      <div class="line"></div>

      <section class="payment">
        <div class="card-display">
          <h3> Payment Information </h3>

          <p class="gray"> Choose your method of payment. </p>

          <div class="card">
            <p>CARD NUMBER</p>
            <p>{{ccn}}</p>

            <img class="card-chip" src="img/card-chip.png" alt="card chip">

            <p>EXPIRATION DATE</p>
            <p>{{exd}}</p>
            <div class="bottom">
              <p>John Doe</p>
              <img class="mastercard" src="img/mastercard.png" alt="master card">
            </div>
          </div>
        </div>
        <div class="details">
          <div class="payment-method">
            <img class="visa" src="img/visa.png" alt="Visa">
            <img class="discover" src="img/discover.png" alt="Discover">
            <span class="checkbox"> </span>
            <img class="paypal" src="img/paypal.png" alt="Paypal">
          </div>

          <div class="form">
            <div class="input">
              <span class="label">Credit Card Number</span>
              <input maxlength="19" type="text" v-model="ccn"
                     placeholder="4324 5433 9382 1030">
            </div>
            <div class="input">
              <span class="label">Expiration Date</span>
              <input type="text" maxlength="5" v-model="exd" placeholder="03/24">
            </div>
            <div class="input">
              <span class="label">Security Code</span>
              <input type="text" v-model="cvv" maxlength="3" placeholder="420">
            </div>
            <div class="input">
              <span class="label">Postal Code</span>
              <input type="text" maxlength="5" v-model="pc" placeholder="10119">
            </div>
          </div>
          <label for="remember" class="remember">

            <span>Use this card for next time purchase</span>
            <input type="checkbox" id="remember" checked hidden>
            <span class="checkbox"></span>
          </label>
          <a class="btn block"> Add Card</a>
        </div>
      </section>

      <div class="line"></div>

      <div class="summary">
        <h4><span>Subtotal</span> <span>N2,497.00</span></h4>
        <h4><span>Estimated TAX</span> <span>N119.64.00</span></h4>
        <h4><span>Promotional Code: <span class="gray"> Z4KXLM9A</span> </span> <span>N2,497.00</span></h4>
      </div>

      <div class="line"></div>

      <div class="total">
        <a class="btn"> Complete Payment </a> <h4>TOTAL: N2556.64</h4>
      </div>
    </div>
  </section>
  <!--=====Payment Ends Here=====-->
</template>

<script>
  export default {
    name: 'app',
    data() {
      return {
        ccn: null,
        cvv: null,
        exd: null,
        pc: null,
      }
    },
    watch: {
      ccn() {
        // remove all non digit characters
        let v = this.ccn.replace(/\D/g, '');

        this.ccn = v.replace(/(\d{4})/, '$1 ').replace(/(\d{4}) (\d{4})/, '$1 $2 ').replace(/(\d{4}) (\d{4}) (\d{4})/, '$1 $2 $3 ');
      },
      cvv() {
        this. cvv = this.cvv.replace(/\D/g, '');
      },
      exd(){
        if(this.exd.length === 2){
          this.exd += '/'
        }
        //this.exd = this.exd.replace(/\D/g, '');
      },
      pc(){
        this.pc = this.pc.replace(/\D/g, '');
      },
    }
  }
</script>
