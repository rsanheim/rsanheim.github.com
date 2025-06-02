# Blog Upgrade Todo List

## ✅ Completed: Modern Jekyll 4.4.1 Upgrade

### High Priority - COMPLETED
- [x] **Upgrade to Ruby 3.4.1** (latest stable, not GitHub Pages compatible)
- [x] **Upgrade Jekyll to 4.4.1** (latest, with GitHub Actions deployment)
- [x] **Update Gemfile** with modern Jekyll setup (replaced github-pages gem)
- [x] **Add GitHub Actions workflow** for production deployment
- [x] **Add development scripts** (`script/server`, `script/lint` with StandardRB)

### Medium Priority - COMPLETED  
- [x] **Test local build** with Jekyll 4.4.1 (2.5x faster: 1.657s → 0.423s)
- [x] **Verify GitHub Actions workflow** builds on all branches
- [x] **Update CLAUDE.md** with new setup documentation

### Decision Made
- [x] **Deployment strategy**: Use GitHub Actions instead of legacy github-pages gem
- [x] **Staging approach**: Build verification on all branches, production deploy on main only

## Future Enhancements

- [ ] Add CircleCI workflow for additional CI/testing
- [ ] Add link checker workflow (expect initial failures)
- [ ] Consider Sass @import deprecation warnings (Dart Sass migration)

---

*Last updated: January 2025*