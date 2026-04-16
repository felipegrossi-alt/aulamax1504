<img width="786" height="282" alt="image" src="https://github.com/user-attachments/assets/7aa029fe-cf8f-4b86-8969-e55bf5ae55e2" />


##  Código Visual Studio dos *Métodos*
class Aluno {
  - idAluno: Long
  - nome: String
  - cpf: String
  - email: String
  - telefone: String
  - endereco: String
  - rfid: String
  - status: String

  + cadastrar(): void
  + atualizar(): void
  + desativar(): void
  + verificarRegularidade(): boolean
  + consultarAgendamentos(): List<Agendamento>
  + consultarAvaliacoes(): List<AvaliacaoFisica>
  + consultarAcessos(): List<Acesso>
}

class Plano {
  - idPlano: Long
  - nome: String
  - tipo: String
  - valor: Double
  - ativo: boolean

  + criar(): void
  + editar(): void
  + ativar(): void
  + desativar(): void
  + listarAtivos(): List<Plano>
}

class Pagamento {
  - idPagamento: Long
  - data: Date
  - valor: Double
  - formaPagamento: String
  - status: String

  + registrar(): void
  + gerarBoleto(): String
  + gerarCartao(): String
  + consultarStatus(): String
  + listarPorAluno(idAluno: Long): List<Pagamento>
}

class Acesso {
  - idAcesso: Long
  - dataHora: DateTime
  - autorizado: boolean

  + registrar(): void
  + validarRfid(rfid: String): boolean
  + listarPorAluno(idAluno: Long): List<Acesso>
  + listarPorPeriodo(inicio: Date, fim: Date): List<Acesso>
}

class Aula {
  - idAula: Long
  - nome: String
  - horario: DateTime
  - capacidadeMaxima: int

  + criar(): void
  + editar(): void
  + cancelar(): void
  + consultarVagasDisponiveis(): int
  + listarHorarios(): List<Aula>
}

class Agendamento {
  - idAgendamento: Long
  - dataReserva: Date
  - status: String

  + reservar(): void
  + cancelar(): void
  + confirmar(): void
  + consultarStatus(): String
  + listarPorAluno(idAluno: Long): List<Agendamento>
}

class Presenca {
  - idPresenca: Long
  - data: Date
  - presente: boolean

  + registrar(): void
  + atualizar(): void
  + listarPorAula(idAula: Long): List<Presenca>
  + listarPorAluno(idAluno: Long): List<Presenca>
}

class AvaliacaoFisica {
  - idAvaliacao: Long
  - data: Date
  - peso: Double
  - imc: Double
  - percentualGordura: Double
  - observacoes: String
  - anexo: String

  + registrar(): void
  + atualizar(): void
  + calcularImc(peso: Double, altura: Double): Double
  + anexarArquivo(arquivo: File): void
  + listarPorAluno(idAluno: Long): List<AvaliacaoFisica>
  + gerarNotificacao(): void
}

class Notificacao {
  - idNotificacao: Long
  - tipo: String
  - dataEnvio: DateTime
  - status: String
  - mensagem: String

  + enviar(): void
  + marcarComoLida(): void
  + listarPorAluno(idAluno: Long): List<Notificacao>
  + enviarVencimentoMensalidade(aluno: Aluno): void
  + enviarConfirmacaoAgendamento(agendamento: Agendamento): void
  + enviarNovaAvaliacao(avaliacao: AvaliacaoFisica): void
}

abstract class Funcionario {
  - idFuncionario: Long
  - nome: String

  + autenticar(senha: String): boolean
  + atualizarDados(): void
}

class Instrutor {
  - especialidade: String

  + registrarPresenca(aula: Aula, aluno: Aluno): void
  + registrarAvaliacao(aluno: Aluno): AvaliacaoFisica
  + listarAulas(): List<Aula>
  + consultarPresencas(idAula: Long): List<Presenca>
}

class Recepcionista {
  + cadastrarAluno(aluno: Aluno): void
  + registrarPagamento(aluno: Aluno): Pagamento
  + gerarBoletoOnline(aluno: Aluno): String
  + consultarRegularidade(idAluno: Long): boolean
}

class Gerente {
  + gerenciarPlano(plano: Plano): void
  + emitirRelatorioInadimplencia(): List<Aluno>
  + emitirRelatorioAlunosAtivos(): List<Aluno>
  + emitirRelatorioAcessos(): List<Acesso>
  + emitirRelatorioOcupacaoAulas(): List<Aula>
}

Funcionario <|-- Instrutor
Funcionario <|-- Recepcionista
Funcionario <|-- Gerente

Aluno "1" -- "1" Plano : contrata
Aluno "1" -- "0..*" Pagamento : realiza
Aluno "1" -- "0..*" Acesso : gera
Aluno "1" -- "0..*" Agendamento : agenda
Aluno "1" -- "0..*" Presenca : possui
Aluno "1" -- "0..*" AvaliacaoFisica : avaliado
Aluno "1" -- "0..*" Notificacao : recebe

Aula "1" -- "0..*" Agendamento : possui
Aula "1" -- "0..*" Presenca : registra

Instrutor "1" -- "0..*" Aula : ministra
Instrutor "1" -- "0..*" AvaliacaoFisica : realiza
Instrutor "1" -- "0..*" Presenca : registra
