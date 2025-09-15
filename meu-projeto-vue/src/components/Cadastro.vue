<template>
  <div class="form-container">
    <h2 class="form-title">Cadastro</h2>
    <form @submit.prevent="validarFormulario" class="form">
      
      <label>Nome Completo</label>
      <input v-model="form.nome" type="text" placeholder="Digite seu nome completo" />

      <label>Data de Nascimento</label>
      <input v-model="form.nascimento" type="date" />

      <label>CPF</label>
      <input v-model="form.cpf" type="text" placeholder="000.000.000-00" />

      <label>Endereço</label>
      <input v-model="form.endereco" type="text" placeholder="Digite seu endereço" />

      <label>Idade</label>
      <input v-model="form.idade" type="number" min="1" />

      <label>E-mail</label>
      <input v-model="form.email" type="email" placeholder="exemplo@email.com" />

      <label>Senha</label>
      <input v-model="form.senha" type="password" placeholder="Digite sua senha" />

      <label>Confirmar Senha</label>
      <input v-model="form.confirmarSenha" type="password" placeholder="Confirme sua senha" />

      <button type="submit" class="btn">Cadastrar</button>

      <p v-if="erro" class="erro">{{ erro }}</p>
      <p v-if="sucesso" class="sucesso">Cadastro realizado com sucesso!</p>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        nome: "",
        nascimento: "",
        cpf: "",
        endereco: "",
        idade: "",
        email: "",
        senha: "",
        confirmarSenha: "",
      },
      erro: "",
      sucesso: false,
    };
  },
  methods: {
    validarFormulario() {
      this.erro = "";
      this.sucesso = false;

      if (!this.form.nome || !this.form.email || !this.form.senha) {
        this.erro = "Preencha todos os campos obrigatórios!";
        return;
      }

      if (this.form.senha !== this.form.confirmarSenha) {
        this.erro = "As senhas não coincidem!";
        return;
      }

      if (!/^\d{3}\.\d{3}\.\d{3}\-\d{2}$/.test(this.form.cpf)) {
        this.erro = "CPF inválido! Use o formato 000.000.000-00";
        return;
      }

      this.sucesso = true;
      console.log("Dados enviados:", this.form);
    },
  },
};
</script>