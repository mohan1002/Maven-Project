package com.wellsfargo.entities;

import javax.persistence.*;
import java.util.Set;

@Entity // Marks this class as a database entity
public class FinancialAdvisor {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY) // Auto-generates ID
    private Long id;

    @Column(nullable = false) // Ensures 'name' cannot be null
    private String name;

    @OneToMany(mappedBy = "financialAdvisor") // Relationship with Client
    private Set<Client> clients;

    // Constructor
    public FinancialAdvisor(String name) {
        this.name = name;
    }

    // Default constructor required by JPA
    public FinancialAdvisor() {}

    // Getters and Setters
    public Long getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Set<Client> getClients() {
        return clients;
    }

    public void setClients(Set<Client> clients) {
        this.clients = clients;
    }
}
