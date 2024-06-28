<script setup>
import { reactive } from 'vue';

const estado = reactive({
  operator: 'plus',
  fieldA: 0,
  fieldB: 0,
  result: 0,
})

const selectOperator = () =>  {
  const { operator, fieldA, fieldB } = estado;
  const parsedFieldA = parseFloat(fieldA);
  const parsedFieldB = parseFloat(fieldB);

  switch (operator) {
    case 'minus':
      estado.result = parsedFieldA - parsedFieldB;
      return estado.result
    case 'times':
      estado.result = parsedFieldA * parsedFieldB;
      return estado.result
    case 'divid':
      estado.result = parsedFieldA / parsedFieldB;
      return estado.result
    default:
      estado.result = parsedFieldA + parsedFieldB;
      return estado.result
  }
}

</script>

<template>
  <div class="container bg-light text-center p-3 mt-3 rounded-4">
    <h1 class="text-secondary mt-3">Arithmetic Calculator</h1>
    <div class="row mt-5">
      <div class="col-md-10">
        <div class="row">
          <div class="col-md-3">
            <input @change="event => estado.fieldA = event.target.value" class="form-control" type="number" required>
          </div>
          <div class="col-md-2">
            <select @change="event => estado.operator = event.target.value" class="form-select text-center px-1 fw-bold">
              <option value="plus" selected>+</option>
              <option value="minus">-</option>
              <option value="times">x</option>
              <option value="divid">÷</option>
            </select>
          </div>
          <div class="col-md-3">
            <input @change="event => estado.fieldB = event.target.value" class="form-control" type="number" required>
          </div>
        </div>
      </div>
      <div class="col-md-2">
        <span class="form-control fw-bold overflow-hidden">{{ selectOperator() }}</span>
      </div>
      </div>
  </div>
</template>