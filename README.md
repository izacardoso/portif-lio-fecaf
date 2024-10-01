CREATE DATABASE faculdade;

USE faculdade;

CREATE TABLE tbl_alunos (
    id_aluno INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    matricula VARCHAR(20) UNIQUE,
    cpf VARCHAR(14) UNIQUE,
    telefone VARCHAR(20),
    email VARCHAR(100),
    endereco VARCHAR(255)
);

CREATE TABLE tbl_cursos (
    id_curso INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    codigo VARCHAR(10) UNIQUE,
    carga_horaria INT
);

CREATE TABLE tbl_materias (
    id_materia INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    codigo VARCHAR(10) UNIQUE,
    carga_horaria INT,
    id_curso INT,
    FOREIGN KEY (id_curso) REFERENCES tbl_cursos(id_curso)
);

CREATE TABLE tbl_professores (
    id_professor INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    cpf VARCHAR(14) UNIQUE,
    telefone VARCHAR(20),
    email VARCHAR(100),
    area_atuacao VARCHAR(100)
);

CREATE TABLE tbl_turmas (
    id_turma INT AUTO_INCREMENT PRIMARY KEY,
    numero_turma VARCHAR(10),
    semestre VARCHAR(10),
    id_curso INT,
    id_professor INT,
    FOREIGN KEY (id_curso) REFERENCES tbl_cursos(id_curso),
    FOREIGN KEY (id_professor) REFERENCES tbl_professores(id_professor)
);

CREATE TABLE tbl_notas (
    id_nota INT AUTO_INCREMENT PRIMARY KEY,
    id_aluno INT,
    id_materia INT,
    nota DECIMAL(5,2),
    semestre VARCHAR(10),
    FOREIGN KEY (id_aluno) REFERENCES tbl_alunos(id_aluno),
    FOREIGN KEY (id_materia) REFERENCES tbl_materias(id_materia)
);
