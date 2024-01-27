<template>
  <div class="class">
    <div class="class--header">
      <img src="../../assets/icons/book-3-line.svg" />
      <div>Cursos</div>
      <CommonInputSearch @search="cursoFilter" />
      <CommonBtn>Ver Todos</CommonBtn>
    </div>
    <div class="tableWrap">
      <table>
        <thead>
          <tr>
            <th>Professor</th>
            <th>Nome do curso</th>
            <th>Progresso</th>
            <th>Status</th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(curso, index) in listFiltrada" :key="index">
            <td class="coluna1">
              <img src="../../assets/images/avatar2.svg" />
              <div>
                <div>
                  {{ curso.professor.nome }}
                </div>
                <div>{{ curso.professor.cargo }}</div>
              </div>
            </td>
            <td class="coluna2">
              <div>
                {{ curso.curso.nome }}
              </div>
              <div>{{ curso.curso.prazo }}</div>
            </td>
            <td class="coluna3">
              <CommonProgressBar :value="curso.progresso" :max="100" />
              {{ curso.progresso }}%
            </td>
            <td>
              <div class="status">
                <img
                  v-if="curso.status === 1"
                  src="../../assets/icons/time-fill.svg"
                />
                <img
                  v-if="curso.status !== 1"
                  src="../../assets/icons/select-box-circle-fill.svg"
                />
                {{ curso.status === 1 ? "Em andamento" : "Concluído" }}
              </div>
            </td>
            <td>
              <img src="../../assets/icons/arrow-right-s-line.svg" />
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script lang="ts" setup>
const cursoList = [
  {
    professor: {
      nome: "Nuray Aksoy",
      cargo: "Gerente de produto",
    },
    curso: {
      nome: "Time Management",
      prazo: "Ago 21 - Set 04",
    },
    progresso: 30,
    status: 1,
  },
  {
    professor: {
      nome: "Arthur Taylor",
      cargo: "CEO",
    },
    curso: {
      nome: "Leadership Skills",
      prazo: "Ago 21 - Set 04",
    },
    progresso: 70,
    status: 1,
  },
  {
    professor: {
      nome: "Lena Müller",
      cargo: "Gerente de marketing",
    },
    curso: {
      nome: "Diversity Training",
      prazo: "Ago 21 - Set 04",
    },
    progresso: 100,
    status: 2,
  },
  {
    professor: {
      nome: "Wei Chen",
      cargo: "Gerente de operações",
    },
    curso: {
      nome: "Efficiency at Work",
      prazo: "Ago 21 - Set 04",
    },
    progresso: 100,
    status: 2,
  },
];
const listFiltrada = ref(cursoList);
const cursoFilter = (search: string) => {
  listFiltrada.value = cursoList.filter((curso) => {
    if (search) {
      return curso.curso.nome.toLowerCase().includes(search.toLowerCase());
    } else {
      return cursoList;
    }
  });
};
</script>

<style lang="scss" scoped>
.class {
  display: flex;
  flex-direction: column;
  row-gap: 16px;
  border-radius: 16px;
  padding: 16px;
  border: 1px solid #e2e4e9;
  box-shadow: 0px 1px 2px 0px rgba(228, 229, 231, 0.24);
  width: calc(100% - 32px);
  height: calc(100% - 32px);

  &--header {
    display: grid;
    align-items: center;
    grid-template-columns: auto 1fr 1fr auto;
    gap: 12px;
  }
}

.coluna1 {
  display: flex;
  align-items: center;
  gap: 12px;

  div {
    max-width: 200px;
    text-overflow: ellipsis;
    overflow: hidden;
    white-space: nowrap;
    div:nth-child(1) {
      color: #0a0d14;
      font-size: 14px;
      font-weight: 400;
    }
    div:nth-child(2) {
      color: #525866;
      font-size: 12px;
      font-weight: 400;
    }
  }

  img {
    width: 40px;
    height: 40px;
  }
}
.coluna2 {
  max-width: 200px;
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
  div:nth-child(1) {
    color: #0a0d14;
    font-size: 14px;
    font-weight: 400;
  }
  div:nth-child(2) {
    color: #525866;
    font-size: 12px;
    font-weight: 400;
  }
}
.coluna3 {
  display: flex;
  align-items: center;
  gap: 8px;
}
.status {
  display: flex;
  padding: 4px 8px 4px 4px;
  justify-content: center;
  align-items: center;
  gap: 4px;
  border-radius: 6px;
  border: 1px solid #e2e4e9;
}
.tableWrap {
  position: relative;
  max-height: 300px;
  overflow: auto;
}

table {
  border: none;
  width: 100%;
  border-spacing: 0px;
}
thead {
  border-radius: 8px;
  background-color: #f6f8fa;
  border: none;
  th {
    text-align: left;
    padding: 8px 12px;

    color: #525866;

    font-size: 14px;
    font-weight: 400;
  }
}
td {
  padding: 12px;
}
</style>
