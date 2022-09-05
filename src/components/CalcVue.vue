<script>
export default {
  data() {
    return {
      qualidades: [
        { qualidade: 5, servico: "5% (INAceitável)" },
        { qualidade: 10, servico: "10% (Not Inaff)" },
        { qualidade: 15, servico: "15% (Okie)" },
        { qualidade: 20, servico: "20% (Bom)" },
        { qualidade: 25, servico: "25% (INAcreditavelmente bom)" },
        { qualidade: 30, servico: "30% (WAH!)" },
      ],
      valor: 0,
      pessoa: 1,
      qld_slc: "",
    };
  },
  computed: {
    final_v() {
      return (
        (this.valor * (1 + this.qld_slc / 100)) /
        this.pessoa
      ).toFixed(2);
    },
  },
};
</script>
<template>
  <div class="titulo"><h1>TAKO BELL</h1></div>
  <main>
    <div class="calc">
      <h1 class="forte"> G O R J E T A S</h1>
      <div class="caixa-valores">
        <label for="input-valor">Qual o valor da conta?</label>
        <input v-model="valor" placeholder="0" id="input-valor" type="number" />
      </div>
      <div class="caixa-valores">
        <label for="select-servico">Como foi o serviço?</label>
        <select
          v-model="qld_slc"
          name="select-qualidade"
          id="select-servico"
        >
          <option disabled value="">Escolha um item</option>
          <option
            v-for="qualidade of qualidades"
            :key="qualidade.qualidade"
            for="select-servico"
            :value="qualidade.qualidade"
          >
            {{ qualidade.servico }}
          </option>
        </select>
      </div>
      <div class="caixa-valores">
        <label for="input-pessoas">Quantas pessoas vão pagar?</label>
        <input
          v-model="pessoa"
          placeholder="1"
          id="input-pessoas"
          type="number"
        />
      </div>
    </div>
    <div class="resultado">
      <h2>Valor da conta:</h2>
      <span>R$ {{ final_v }} por pessoa</span>
    </div>
  </main>
</template>
