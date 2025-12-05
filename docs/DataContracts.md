# Data Contracts

## 1. Repository Entity

```kotlin
data class Repository(
    val id: Long,
    val name: String,
    val description: String?,
    val visibility: Visibility,
    val defaultBranch: String,
    val isPrivate: Boolean,
    val createdAt: Date,
    val updatedAt: Date
)
```

## 2. Repository Creation Request

```kotlin
data class CreateRepositoryRequest(
    val name: String,
    val description: String?,
    val isPrivate: Boolean,
    val hasIssues: Boolean,
    val hasWiki: Boolean,
    val hasDownloads: Boolean,
    val autoInit: Boolean,
    val gitignoreTemplate: String?,
    val licenseTemplate: String?
)
```

## 3. Authentication Token

```kotlin
data class AuthToken(
    val accessToken: String,
    val tokenType: String,
    val scope: String,
    val expiresAt: Long?
)
```

## 4. API Response Models

### 4.1 Repository Creation Response
```kotlin
data class RepositoryResponse(
    val id: Long,
    val name: String,
    val fullName: String,
    val description: String?,
    val private: Boolean,
    val htmlUrl: String,
    val cloneUrl: String,
    val defaultBranch: String,
    val createdAt: String,
    val updatedAt: String
)
```

## 5. State Models

### 5.1 Repository Creation State
```kotlin
data class RepositoryCreationState(
    val isLoading: Boolean = false,
    val success: Boolean = false,
    val error: String? = null,
    val repository: Repository? = null
)
```

### 5.2 Wizard State
```kotlin
data class CreationWizardState(
    val step: Int = 0,
    val repositoryName: String = "",
    val description: String = "",
    val isPrivate: Boolean = true,
    val initializeWithReadme: Boolean = true,
    val initializeWithGitignore: Boolean = false,
    val selectedLicense: String? = null
)
```

## 6. Repository Interface

```kotlin
interface RepositoryRepository {
    suspend fun createRepository(request: CreateRepositoryRequest): Result<Repository>
    suspend fun getRepositories(): Result<List<Repository>>
    suspend fun getRepository(id: Long): Result<Repository>
    suspend fun authenticate(token: String): Result<AuthToken>
}
```