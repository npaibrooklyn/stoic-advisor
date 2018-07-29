<template>
  <div>
    <form v-if="!isSubmitted" @submit.prevent="submit" novalidate>
      <div class="form-group">
        <label for="name">{{ $t('form.name') }} *</label>
        <input type="text" class="form-control" id="name" v-model.lazy.trim="form.name" @blur="onFieldBlur('name')" v-bind:class="getFieldClasses('name')">
        <div v-if="isErrorField('name')" class="invalid-feedback">{{ $t('error.fieldRequired', { field: $t('form.name') }) }}</div>
      </div>
      <div class="form-group">
        <label for="email">{{ $t('form.email') }} *</label>
        <input type="email" class="form-control" id="email" v-model.lazy.trim="form.email" @blur="onFieldBlur('email')" v-bind:class="getFieldClasses('email')">
        <div v-if="isErrorField('email')" class="invalid-feedback">{{ $t('error.fieldInvalid', { field: $t('form.email') }) }}</div>
      </div>
      <div class="form-group">
        <label for="question">{{ $t('form.question') }} *</label>
        <textarea 
          type="question"
          rows="12" 
          class="form-control" 
          id="question" 
          v-model.trim="form.question" 
          v-bind:class="getFieldClasses('question')" 
          v-bind:maxlength="$v.form['question'].$params.maxLength.max" 
          @blur="onFieldBlur('question')">
        </textarea>
        <small class="text-muted form-text">{{ $tc('form.charactersLeft', getCharactersLeft('question'), { charCount: getCharactersLeft('question') }) }}</small>
        <div v-if="isErrorField('question')" class="invalid-feedback">{{ $t('error.fieldInvalid', { field: $t('form.question') }) }}</div>
      </div>
      <div class="alert alert-danger" v-if="isError">
        <p class="mb-0">
          <strong>{{ $t(errorHeader) }}</strong>
        </p>
        <ul class="mb-0 pl-3" v-if="errors.length > 0">
          <li v-for="error in errors" v-bind:key="error.field">
            <span v-if="error.field">{{ $t('form.'+error.field) }}<span v-if="error.message">: {{ $t(error.message) }}</span></span>
            <span v-else-if="error.message">{{ $t(error.message) }}</span>
          </li>
        </ul>
      </div>
      <div class="form-group">
        <button type="submit" class="btn btn-primary" :disabled="submitting">
          <span v-if="submitting">{{ $t('form.submitting' ) }} <img src="../../assets/loader.svg" /></span>
          <span v-else>{{ $t('form.submit' ) }}</span>
        </button>
      </div>
    </form>
    <div v-else>
      <div class="alert alert-success">
        <strong>{{ $t('form.submitted' ) }}</strong>
      </div>
      <div class="alert alert-info">
        <p><strong>{{ $t('form.sentInfo' ) }}</strong></p>
        <pre>
            {{form}}
        </pre>
      </div>
      <p class="text-center">
        <a href="#" class="btn btn-secondary" @click.prevent="reload()">{{ $t('form.return' ) }}</a>
      </p>
    </div>
  </div>
</template>

<script src="./Form.js"></script>
<style src="./Form.scss" lang="scss" scoped></style>
