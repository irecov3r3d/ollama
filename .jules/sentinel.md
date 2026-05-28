## 2026-05-28 - Replace math/rand with crypto/rand for ID generation
**Vulnerability:** The application was using the weak random number generator `math/rand` to generate IDs (`cmpl-123`, `chatcmpl-123`, `resp_123456`, `call_abcdefgh`) in `middleware/openai.go`, `openai/responses.go` and `server/routes.go`.
**Learning:** This is a common security pitfall where developers use `math/rand` for convenience when generating strings or IDs, which can lead to predictability and potential security risks such as collision or brute force attacks.
**Prevention:** Always use `crypto/rand` for generating security-sensitive or collision-sensitive values like session IDs, tokens, or unique identifiers. Use `crypto/rand.Read` and hex-encode the result for a secure and standard ID format.
